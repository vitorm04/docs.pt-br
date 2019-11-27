---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450880"
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

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>Exemplos

- Instale o SDK do .NET Core 2,2: `dotnet-sdk-2.2`
- Instale o tempo de execução do ASP.NET Core 3,0: `aspnetcore-runtime-3.0`
- Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`

### <a name="troubleshoot"></a>Solução de problemas

Se a combinação de pacote não funcionar, ela não estará disponível. Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core. O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`
