---
ms.openlocfilehash: 07dd58c314c826c426193b829ea1f64669fb888b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594561"
---

Os [scripts dotnet-install](../../tools/dotnet-install-script.md) são usados para instalações de automação e não administrativas do **SDK** e do **tempo de execução**. É possível baixar o script em <https://dot.net/v1/dotnet-install.sh>.

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) do SDK, que é o .net 3,1. Para instalar a versão atual, que pode não ser uma versão (LTS), use o `-c Current` parâmetro.

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
