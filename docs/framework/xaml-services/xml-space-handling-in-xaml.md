---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458797"
---
# <a name="xmlspace-handling-in-xaml"></a>Tratamento de xml:space em XAML
O atributo `xml:space` é um atributo definido por XML que declara o comportamento significativo de processamento de espaço em branco dentro de um elemento Object. Esse comportamento é relevante para todo o conteúdo (texto interno) contido no elemento em que `xml:space` é declarado, além de escopos para elementos filho.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- ou -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Comentários  
 A definição para o atributo `xml:space` em XAML, incluindo seus dois valores possíveis, é derivada de `xml:space` conforme definido como um "atributo especial" pelas especificações do W3C para XML.  
  
 O valor padrão do atributo `xml:space` é o valor literal `"default"`. Para o valor `"default"`, ou se `xml:space` não for indicado, o comportamento da análise de espaço em branco significativa é o tratamento padrão, conforme definido no tópico [processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md).  
  
 Para preservar o espaço em branco no conteúdo do elemento de objeto, especifique `xml:space="preserve"` nesse elemento de objeto.  
  
 Na maioria das interpretações, os efeitos de atributo `xml:space` e o valor do atributo têm como escopo os elementos filho.  
  
 Para obter uma discussão completa sobre o processamento de espaço em branco em XAML, consulte [processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Consulte também

- [Processamento de espaço em branco em XAML](whitespace-processing-in-xaml.md)
- [Visão geral de XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
