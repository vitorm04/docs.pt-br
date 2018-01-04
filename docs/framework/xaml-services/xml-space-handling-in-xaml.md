---
title: Tratamento de xml:space em XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], whitespace processing
- xml:space attribute [XAML Services]
- whitespace processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
caps.latest.revision: "15"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b8356cdb47b6b834e8d9a6bb84b26445af6d865
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="xmlspace-handling-in-xaml"></a>Tratamento de xml:space em XAML
O `xml:space` é um atributo definido pelo XML que declara o comportamento de processamento de espaço em branco significativo dentro de um elemento de objeto. Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento onde `xml:space` é declarado e também para elementos filho.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- ou -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Comentários  
 A definição para o `xml:space` atributo em XAML, incluindo seus dois valores possíveis é derivado de `xml:space` como definido como um "atributo especial" por especificações de W3C XML.  
  
 O valor padrão de `xml:space` atributo é o valor literal `"default"`. Para o valor `"default"`, ou se `xml:space` não é indicado, o comportamento de análise de espaço em branco significativo é a manipulação do padrão, conforme definido no tópico [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Para preservar espaço em branco dentro do conteúdo de elemento de objeto, especifique `xml:space="preserve"` naquele elemento.  
  
 Na maioria dos interpretações, o `xml:space` efeitos de atributo e o valor do atributo passam para elementos filho.  
  
 Para obter uma discussão completa de espaços em branco em XAML de processamento, consulte [processamento de espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Consulte também  
 [Processamento de Espaço em branco em XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)  
 [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
