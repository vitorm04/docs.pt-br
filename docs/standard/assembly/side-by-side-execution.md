---
title: Assemblies e execução lado a lado
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4f246108768dcebf51348f67c4523cb83df4f9d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053975"
---
# <a name="assemblies-and-side-by-side-execution"></a>Assemblies e execução lado a lado

Execução lado a lado é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador. Isso significa que você pode ter várias versões do tempo de execução e várias versões de aplicativos e componentes que usam uma versão do tempo de execução no mesmo computador ao mesmo tempo. A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do tempo de execução um aplicativo usa.  
  
O suporte para armazenamento lado a lado e execução de diferentes versões do mesmo assembly é uma parte integrante da nomenclatura forte e está integrada à infraestrutura do tempo de execução. Como o número de versão do assembly de nome forte faz parte de sua identidade, o tempo de execução pode armazenar várias versões do mesmo assembly no cache de assembly global e carregar esses módulos em tempo de execução.  
  
Embora o tempo de execução ofereça a capacidade de criar aplicativos lado a lado, a execução lado a lado não é automática. Para obter mais informações sobre como criar aplicativos para execução lado a lado, consulte [diretrizes para criar componentes para execução lado a lado](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Consulte também

- [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblies no .NET](index.md)
