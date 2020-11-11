---
ms.openlocfilehash: f8bf759272ad75b6684496a913cdef7f7912286d
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506788"
---

Os [scripts dotnet-install](../../tools/dotnet-install-script.md) são usados para instalações de automação e não administrativas do **SDK** e do **tempo de execução**. É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) do SDK, que é o .NET 5,0. Para instalar a versão atual, que pode não ser uma versão (LTS), use o `-c Current` parâmetro.

```bash
./dotnet-install.sh -c Current
```

Para instalar o tempo de execução do .NET em vez do SDK, use o `--runtime` parâmetro.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Você pode instalar uma versão específica alterando o `-c` parâmetro para indicar a versão específica. O comando a seguir instala o SDK do .NET 5,0.

```bash
./dotnet-install.sh -c 5.0
```

Para obter mais informações, consulte [dotnet – referência de scripts de instalação](../../tools/dotnet-install-script.md).
