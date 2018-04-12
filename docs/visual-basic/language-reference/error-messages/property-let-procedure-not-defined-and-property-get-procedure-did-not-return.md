---
title: Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b043ca698a9c90afd41de90c7dbc5879ae7de623
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a>Procedimento let de propriedade não definido e procedimento get de propriedade não retornou um objeto
Certas propriedades, métodos e operações só podem se aplicam a `Collection` objetos. Você especificou uma operação ou propriedade que é exclusiva a coleções, mas o objeto não é uma coleção.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique a ortografia do nome do objeto ou propriedade, ou verifique se o objeto é um `Collection` objeto.  
  
2.  Examine o `Add` método usado para adicionar o objeto à coleção para certificar-se de que a sintaxe está correto e que quaisquer identificadores foram escritos corretamente.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Collection>
