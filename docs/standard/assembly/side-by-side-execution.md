---
title: Assemblies e execução lado a lado
description: Saiba mais sobre a execução lado a lado, que é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 74b5710c7e8ad60873fb83a3699ce3992ead6e07
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378638"
---
# <a name="assemblies-and-side-by-side-execution"></a>Assemblies e execução lado a lado

Execução lado a lado é a capacidade de armazenar e executar várias versões de um aplicativo ou componente no mesmo computador. Isso significa que você pode ter várias versões do runtime e várias versões de aplicativos e componentes que usam uma versão do runtime no mesmo computador ao mesmo tempo. A execução lado a lado confere mais controle sobre a quais versões de um componente um aplicativo está associado e mais controle sobre qual versão do runtime um aplicativo usa.  
  
O suporte para armazenamento lado a lado e execução de diferentes versões do mesmo assembly é uma parte integrante da nomenclatura forte e está integrada à infraestrutura do runtime. Como o número de versão do assembly de nome forte faz parte de sua identidade, o runtime pode armazenar várias versões do mesmo assembly no cache de assembly global e carregar esses módulos em runtime.  
  
Embora o runtime ofereça a capacidade de criar aplicativos lado a lado, a execução lado a lado não é automática. Para obter mais informações sobre como criar aplicativos para execução lado a lado, consulte [diretrizes para criar componentes para execução lado a lado](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).  
  
## <a name="see-also"></a>Confira também

- [Como o tempo de execução localiza assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [Assemblies no .NET](index.md)
