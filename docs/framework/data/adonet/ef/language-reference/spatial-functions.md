---
title: Funções espaciais
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078273"
---
# <a name="spatial-functions"></a><span data-ttu-id="dfdd5-102">Funções espaciais</span><span class="sxs-lookup"><span data-stu-id="dfdd5-102">Spatial Functions</span></span>
<span data-ttu-id="dfdd5-103">Não há nenhum formato literal para tipos espaciais.</span><span class="sxs-lookup"><span data-stu-id="dfdd5-103">There is no literal format for spatial types.</span></span> <span data-ttu-id="dfdd5-104">Entretanto, você pode usar funções canônicas do Entity Framework que você chama usando cadeias de caracteres no formato de texto bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="dfdd5-104">However, you can use canonical Entity Framework functions that you call using strings in Well-Known Text format.</span></span> <span data-ttu-id="dfdd5-105">Por exemplo, a chamada de função a seguir cria um ponto geométrico:</span><span class="sxs-lookup"><span data-stu-id="dfdd5-105">For example, the following function call creates a geometry point:</span></span>  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 <span data-ttu-id="dfdd5-106">O [métodos SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) página lista todos os métodos do Entity Framework canônicos espaciais.</span><span class="sxs-lookup"><span data-stu-id="dfdd5-106">The [SpatialEdmFunctions Methods](https://msdn.microsoft.com/library/hh749531.aspx) page lists all spatial canonical Entity Framework methods.</span></span> <span data-ttu-id="dfdd5-107">Clique em um método de interesse ver quais parâmetros devem ser passados para uma função.</span><span class="sxs-lookup"><span data-stu-id="dfdd5-107">Click on a method of interest to see what parameters should be passed to a function.</span></span>
