---
ms.openlocfilehash: dece035f443ff827a250ca1c1233b7651df7d108
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424707"
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