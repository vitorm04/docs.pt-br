---
title: Muitos clientes de aplicativo de DLL
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a>Muitos clientes de aplicativo de DLL
A biblioteca de vínculo dinâmico (DLL) para [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] somente pode acomodar acesso por um número limitado de aplicativos de host. Seu aplicativo e outros aplicativos que são [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (alguns dos quais podem ser acessados pelo seu aplicativo) de hosts estão tentando acessar o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL ao mesmo tempo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Reduza o número de aplicativos abertos acessando [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)
