---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77466109"
---

Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}`.

- \ do **produto**
O tipo de produto .NET a ser instalado. As opções válidas são:

  - dotnet
  - aspnetcore

- **tipo**\
Escolhe o SDK ou o tempo de execução. As opções válidas são:

  - sdk
  - runtime

- **versão**\
A versão do SDK ou do tempo de execução a ser instalado. Este artigo sempre fornecerá as instruções para a versão mais recente com suporte. As opções válidas são qualquer versão lançada, como:

  - 3.1
  - 3.0
  - 2.1

  É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição do Linux. Para obter uma lista de distribuições com suporte, consulte [dependências e requisitos do .NET Core](../dependencies.md?pivots=os-linux).

### <a name="examples"></a>Exemplos

- Instale o tempo de execução do ASP.NET Core 3,1: `aspnetcore-runtime-3.1`
- Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`
- Instale o SDK do .NET Core 3,0: `dotnet-sdk-3.0`

### <a name="package-missing"></a>Pacote ausente

Se a combinação de versão do pacote não funcionar, ela não estará disponível. Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core. O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`. Para obter uma lista de distribuições do Linux com suporte no .NET Core, confira [dependências e requisitos do .NET Core](../dependencies.md?pivots=os-linux).
