---
ms.openlocfilehash: 85f50b221e7ecb1ebd6fa539894ab7aabed8d362
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67540077"
---
### <a name="install-the-global-tool"></a>Instalar a ferramenta global

Os ativos de pacote devem ser instalados em um local protegido usando a opção `--tool-path`. Essa separação evita o compartilhamento de um ambiente de usuário restrito com um ambiente com privilégios elevados.

```bash
sudo dotnet tool install PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

`/usr/local/share/dotnet-tools` será criado com a permissão `drwxr-xr-x`. Se o diretório já existir, use o comando `ls -l` para verificar se o usuário restrito não tem permissão para editar o diretório. Nesse caso, use o comando `sudo chmod o-w -R /usr/share/dotnet-tools` para remover o acesso.

### <a name="run-the-global-tool"></a>Executar a ferramenta global

**Opção 1** Usar o caminho completo com o sudo:

```bash
sudo /usr/local/share/dotnet-tools/TOOLCOMMAND
```

**Opção 2** Adicionar o link do símbolo da ferramenta, uma vez por ferramenta:

```bash
sudo ln -s /usr/local/share/dotnet-tools/TOOLCOMMAND /usr/local/bin/TOOLCOMMAND
```

E execute com:

```bash
sudo TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Desinstalar a ferramenta global

```bash
sudo dotnet tool uninstall PACKAGEID --tool-path /usr/local/share/dotnet-tools
```

Se tiver feito um link de símbolo, você também precisará removê-lo:

```bash
sudo rm /usr/local/bin/TOOLCOMMAND
```
