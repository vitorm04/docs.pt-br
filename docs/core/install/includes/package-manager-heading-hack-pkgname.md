---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134097"
---

Os pacotes adicionados aos feeds do gerenciador `{product}-{type}-{version}`de pacotes são nomeados em um formato hackeável: .

- **Produto**\
O tipo de produto .NET a ser instalado. As opções válidas são:

  - dotnet
  - aspnetcore

- **Tipo**\
Escolhe o SDK ou o tempo de execução. As opções válidas são:

  - sdk
  - runtime

- **Versão**\
A versão do SDK ou tempo de execução para instalar. Este artigo sempre dará as instruções para a versão mais recente suportada. Opções válidas são qualquer versão lançada, tais como:

  - 3.1
  - 3.0
  - 2.1

  É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição Linux. Para obter uma lista de distribuições suportadas, consulte [as dependências e os requisitos do .NET Core](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Exemplos

- Instale o tempo de execução do ASP.NET Core 3.1:`aspnetcore-runtime-3.1`
- Instale o tempo de execução do .NET Core 2.1:`dotnet-runtime-2.1`
- Instale o .NET Core 3.1 SDK:`dotnet-sdk-3.1`

### <a name="package-missing"></a>Pacote ausente

Se a combinação de versão de pacote não funcionar, ela não está disponível. Por exemplo, não há uma ASP.NET SDK Core, os componentes do SDK estão incluídos no .NET Core SDK. O `aspnetcore-sdk-2.2` valor está incorreto e deve ser `dotnet-sdk-2.2`. Para obter uma lista de distribuições Linux suportadas pelo .NET Core, consulte [as dependências e requisitos do .NET Core](../dependencies.md?pivots=os-linux).
