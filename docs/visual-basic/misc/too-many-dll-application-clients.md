---
title: Muitos clientes do aplicativo DLL | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1abc9ce574de00db42a33cde478ca80be74e61ff
ms.lasthandoff: 03/13/2017

---
# <a name="too-many-dll-application-clients"></a>Muitos clientes de aplicativo de DLL
A biblioteca de vínculo dinâmico (DLL) para [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] possa acomodar somente acesso por um número limitado de aplicativos de host. Seu aplicativo e outros aplicativos que são [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] hosts (alguns dos quais podem ser acessados pelo seu aplicativo) estão tentando acessar o [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] DLL ao mesmo tempo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Reduza o número de aplicativos abertos acessando [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Tipos de Erro](../../visual-basic/programming-guide/language-features/error-types.md)
