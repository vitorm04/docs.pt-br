---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116162"
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

### <a name="troubleshoot"></a>Solução de problemas

Se a combinação de pacote não funcionar, ela não estará disponível. Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core. O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`
