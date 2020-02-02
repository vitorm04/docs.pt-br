---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920657"
---

Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}`.

- \ do **produto**
O tipo de produto .NET a ser instalado. As opções válidas são:

  - dotnet
  - aspnetcore

- **tipo**\
Escolhe o SDK ou o tempo de execução. As opções válidas são:

  - sdk
  - Tempo de execução do

- **versão**\
A versão do SDK ou do tempo de execução a ser instalado. Este artigo sempre fornecerá as instruções para a versão mais recente com suporte. As opções válidas são qualquer versão lançada, como:

  - 3.0
  - 2.2
  - 2.1

### <a name="examples"></a>Exemplos

- Instale o SDK do .NET Core 2,2: `dotnet-sdk-2.2`
- Instale o tempo de execução do ASP.NET Core 3,1: `aspnetcore-runtime-3.1`
- Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`

### <a name="package-missing"></a>Pacote ausente

Se a combinação de versão do pacote não funcionar, ela não estará disponível. Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core. O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`.
