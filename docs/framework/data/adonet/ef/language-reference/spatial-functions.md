---
title: Funções espaciais
ms.date: 03/30/2017
ms.assetid: 90cb177d-88a0-45be-97e8-3b306283c6e0
ms.openlocfilehash: ad6b722e84aae40354e30434b107752d02352645
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266382"
---
# <a name="spatial-functions"></a>Funções espaciais
Não há nenhum formato literal para tipos espaciais. Entretanto, você pode usar funções canônicas do Entity Framework que você chama usando cadeias de caracteres no formato de texto bem conhecido. Por exemplo, a chamada de função a seguir cria um ponto geométrico:  
  
```  
GeometryFromText('POINT (43 -73)')  
```  
  
 O [métodos SpatialEdmFunctions](https://msdn.microsoft.com/library/hh749531.aspx) página lista todos os métodos do Entity Framework canônicos espaciais. Clique em um método de interesse ver quais parâmetros devem ser passados para uma função.
