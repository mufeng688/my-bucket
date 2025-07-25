
### **将自建仓库添加到本地 Scoop**

1.  **运行 `scoop bucket add` 命令**：
    ```powershell
    scoop bucket add <自定义仓库名> <你的Git仓库URL>
    ```
    *   `<自定义仓库名>`: 这是你在本地为这个仓库取的别名，例如 `mybucket`。
    *   `<你的Git仓库URL>`: 就是你在第一步中创建的仓库的 URL。

    **示例：**
    ```powershell
    scoop bucket add mybucket https://github.com/mufeng688/my-bucket.git
    ```
    添加成功后，Scoop 会自动将你的仓库克隆到 `scoop\buckets` 目录下。

2.  **查看已添加的仓库**：
    ```powershell
    scoop bucket list
    ```
    你应该能在列表中看到你刚刚添加的 `mybucket`。

---

### **安装和使用仓库中的软件**

现在，你可以像安装官方软件一样安装你自己仓库里的软件了。

1.  **安装软件**：
    ```powershell
    scoop install my-app
    ```
    Scoop 会自动在所有已添加的仓库中搜索名为 `my-app` 的软件。

2.  **指定仓库安装**（推荐，避免重名冲突）：
    ```powershell
    scoop install mybucket/my-app
    ```

### **进阶：维护和更新**

*   **更新软件版本**：当 `my-app` 发布了新版本（如 `1.2.4`），你只需要：
    1.  修改本地仓库中的 `my-app.json` 文件，更新 `version`, `url`, 和 `hash` 字段。
    2.  将修改 `commit` 并 `push` 到你的 Git 仓库。
    3.  在你的电脑上运行 `scoop update`，Scoop 就会拉取你仓库的最新清单。
    4.  运行 `scoop update my-app` 来更新已安装的软件。
