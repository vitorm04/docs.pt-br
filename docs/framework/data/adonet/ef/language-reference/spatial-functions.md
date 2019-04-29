---
title: Funções espaciais
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: 09402633c5e7f591a534992fc92655e6a2d1d88d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797690"
---
# <a name="spatial-functions"></a><span data-ttu-id="e1d73-102">Funções espaciais</span><span class="sxs-lookup"><span data-stu-id="e1d73-102">Spatial Functions</span></span>
<span data-ttu-id="e1d73-103">Não há nenhum formato literal para tipos espaciais.</span><span class="sxs-lookup"><span data-stu-id="e1d73-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="e1d73-104">Entretanto, você pode usar funções canônicas do Entity Framework que você chama usando cadeias de caracteres no formato de texto bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="e1d73-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="e1d73-105">Por exemplo, a chamada de função a seguir cria um ponto geométrico:</span><span class="sxs-lookup"><span data-stu-id="e1d73-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="e1d73-106">O <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> métodos têm todos os métodos do Entity Framework canônicos espaciais.</span><span class="sxs-lookup"><span data-stu-id="e1d73-106">The <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> methods have all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="e1d73-107">Clique em um método de interesse ver quais parâmetros devem ser passados para uma função.</span><span class="sxs-lookup"><span data-stu-id="e1d73-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
