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
# <a name="spatial-functions"></a>Funções espaciais
Não há nenhum formato literal para tipos espaciais. Entretanto, você pode usar funções canônicas do Entity Framework que você chama usando cadeias de caracteres no formato de texto bem conhecido. Por exemplo, a chamada de função a seguir cria um ponto geométrico:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 O <xref:System.Data.Common.CommandTrees.ExpressionBuilder.Spatial.SpatialEdmFunctions> métodos têm todos os métodos do Entity Framework canônicos espaciais. Clique em um método de interesse ver quais parâmetros devem ser passados para uma função.
