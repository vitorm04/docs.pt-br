---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: a7c3775f2e49a80eabc61f24d086a94fcadfd574
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617571"
---
# <a name="xmlspace-handling-in-xaml"></a>Tratamento de xml:space em XAML
O `xml:space` é um atributo definido pelo XML que declara o comportamento de processamento significativo de espaço em branco dentro de um elemento de objeto. Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento onde `xml:space` é declarada e também para os elementos filho.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- ou -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Comentários  
 A definição para o `xml:space` atributo no XAML, incluindo seus dois valores possíveis é derivado de `xml:space` conforme definido como um "atributo especial" pelas especificações de W3C para XML.  
  
 O valor padrão de `xml:space` atributo é o valor literal `"default"`. Para o valor `"default"`, ou se `xml:space` não é indicado, o comportamento de análise de espaço em branco significativo é a manipulação de padrão, conforme definido no tópico [XAML de processamento de espaço em branco](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
 Para preservar espaço em branco dentro do conteúdo de elemento de objeto, especifique `xml:space="preserve"` nesse elemento de objeto.  
  
 Na maioria dos interpretações, o `xml:space` efeitos do atributo e o valor do atributo limitam-se aos elementos filho.  
  
 Para obter uma discussão completa sobre o espaço em branco em XAML de processamento, consulte [XAML de processamento de espaço em branco](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Consulte também
- [Espaço em branco em XAML de processamento](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)
- [Visão geral de XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
