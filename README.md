<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Website Visualization</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            background-color: #f4f4f4;
        }

        h1 {
            margin: 20px 0;
            color: #333;
        }

        #tree-container {
            margin: 20px;
            display: flex;
            justify-content: center;
        }

        .node {
            padding: 10px;
            background-color: #4CAF50;
            color: white;
            border-radius: 5px;
            text-align: center;
            margin: 10px;
            width: 100px;
        }

        .node:hover {
            background-color: #45a049;
            cursor: pointer;
        }

        .line {
            width: 2px;
            background-color: #000;
            position: absolute;
        }

        .tree {
            display: flex;
            flex-direction: column;
            align-items: center;
            position: relative;
        }

        .children {
            display: flex;
            justify-content: center;
            margin-top: 20px;
        }

        .line {
            height: 20px;
        }
    </style>
</head>
<body>
    <h1>Website Visualization</h1>
    <div id="tree-container"></div>

    <script>
        const treeData = {
            name: "Home",
            children: [
                {
                    name: "About",
                    children: [
                        { name: "Team" },
                        { name: "History" }
                    ]
                },
                {
                    name: "Services",
                    children: [
                        { name: "Web Design" },
                        { name: "SEO" },
                        { name: "Marketing" }
                    ]
                },
                {
                    name: "Contact",
                    children: []
                }
            ]
        };

        function createTreeNode(node, container) {
            const nodeElement = document.createElement("div");
            nodeElement.classList.add("node");
            nodeElement.innerText = node.name;
            container.appendChild(nodeElement);

            if (node.children && node.children.length > 0) {
                const childrenContainer = document.createElement("div");
                childrenContainer.classList.add("children");
                container.appendChild(childrenContainer);

                node.children.forEach(child => {
                    const childContainer = document.createElement("div");
                    childContainer.classList.add("tree");
                    childrenContainer.appendChild(childContainer);

                    createTreeNode(child, childContainer);
                });
            }
        }

        const treeContainer = document.getElementById("tree-container");
        createTreeNode(treeData, treeContainer);
    </script>
</body>
</html>
