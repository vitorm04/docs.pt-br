---
title: Muitos clientes de aplicativo de DLL
ms.date: 07/20/2015
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
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a><span data-ttu-id="07afd-102">Muitos clientes de aplicativo de DLL</span><span class="sxs-lookup"><span data-stu-id="07afd-102">Too many DLL application clients</span></span>
<span data-ttu-id="07afd-103">A biblioteca de vínculo dinâmico (DLL) para [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] somente pode acomodar acesso por um número limitado de aplicativos de host.</span><span class="sxs-lookup"><span data-stu-id="07afd-103">The dynamic-link library (DLL) for [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can only accommodate access by a limited number of host applications.</span></span> <span data-ttu-id="07afd-104">Seu aplicativo e outros aplicativos que são [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] (alguns dos quais podem ser acessados pelo seu aplicativo) de hosts estão tentando acessar o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="07afd-104">Your application and other applications that are [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hosts (some of which may be accessed by your application) are all attempting to access the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] DLL at the same time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07afd-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="07afd-105">To correct this error</span></span>  
  
-   <span data-ttu-id="07afd-106">Reduza o número de aplicativos abertos acessando [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07afd-106">Reduce the number of open applications accessing [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07afd-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07afd-107">See Also</span></span>  
 [<span data-ttu-id="07afd-108">Tipos de Erro</span><span class="sxs-lookup"><span data-stu-id="07afd-108">Error Types</span></span>](../../visual-basic/programming-guide/language-features/error-types.md)
