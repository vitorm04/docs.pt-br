---
title: Tratamento de xml:space em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071433"
---
# <a name="xmlspace-handling-in-xaml"></a>Tratamento de xml:space em XAML

O `xml:space` atributo é um atributo definido por XML que declara o comportamento significativo de processamento de espaço branco dentro de um elemento objeto. Esse comportamento é relevante para todo o conteúdo `xml:space` (texto interno) contido no elemento onde é declarado, e também escopos para elementos infantis.

## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML

```xaml
<object xml:space="preserve" />
```

 \- ou –

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>Comentários

A definição `xml:space` para o atributo em XAML, `xml:space` incluindo seus dois valores possíveis, é derivada de como definido como um "atributo especial" pelas especificações W3C para XML.

O valor padrão `xml:space` do atributo `"default"`é o valor literal. Para o `"default"`valor `xml:space` , ou se não for indicado, o comportamento de análise significativa do espaço branco é o manuseio padrão, conforme definido no tópico [Processamento de espaço branco em XAML](white-space-processing.md).

Para preservar o espaço em `xml:space="preserve"` branco dentro do conteúdo do elemento objeto, especifique nesse elemento do objeto.

Na maioria das `xml:space` interpretações, os efeitos atributos e o valor do atributo são escopo de elementos infantis.

Para uma discussão completa sobre o processamento do espaço branco em XAML, consulte [o processamento de espaço branco em XAML](white-space-processing.md).

## <a name="see-also"></a>Confira também

- [Processamento de espaço em branco em XAML](white-space-processing.md)
- [Visão geral de XAML (WPF)](../fundamentals/xaml.md)
