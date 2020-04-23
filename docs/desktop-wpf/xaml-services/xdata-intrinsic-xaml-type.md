---
title: Tipo intrínseco x:XData (XAML)
ms.date: 03/30/2017
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
ms.openlocfilehash: b7f0954158988db107feb4a6c51ba81d5db11dcb
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071538"
---
# <a name="xxdata-intrinsic-xaml-type"></a>Tipo intrínseco x:XData (XAML)
Permite a colocação de ilhas de dados XML dentro de uma produção XAML. Os elementos `x:XData` XML dentro não devem ser tratados por processadores XAML como se fossem parte do namespace xaml padrão de ação ou qualquer outro espaço de nome XAML. `x:XData`pode conter XML arbitrário bem formado.

## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML

```xaml
<x:XData>
  <elementDataRoot>
    [elementData]
  </elementDataRoot>
</x:XData>
```

## <a name="xaml-values"></a>Valores XAML

|||
|-|-|
|`elementDataRoot`|O único elemento raiz da ilha de dados fechado. Para a maioria dos consumidores eventuais, XML que não tem uma única raiz é considerado inválido. Em particular, uma única raiz `x:XData` é necessária se a destinação como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.|
|`[elementData]`|Opcional. XML que representa os dados XML. Qualquer número de elementos pode ser contido como dados de elementos e elementos aninhados podem ser contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.|

## <a name="remarks"></a>Comentários

Os elementos XML dentro de um `x:XData` objeto podem redeclarar todos os espaços de nome e prefixos possíveis do XMLDOM contendo dentro dos dados.

O acesso programático aos `x:XData` dados XML e ao tipo XAML intrínseco <xref:System.Windows.Markup.XData> é possível em Serviços .NET XAML através da classe.

## <a name="wpf-usage-notes"></a>Notas de uso do WPF

O `x:XData` objeto é usado principalmente como <xref:System.Windows.Data.XmlDataProvider>objeto infantil de um , ou <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> alternativamente, como objeto filho da propriedade (em XAML, isso é tipicamente expresso em sintaxe de elemento de propriedade).

Os dados devem normalmente redefinir o namespace xml base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma seqüência de string vazia). Isso é mais fácil para <xref:System.Windows.Data.Binding.XPath%2A> ilhas de dados simples porque as expressões que são usadas para referenciar e vincular aos dados podem evitar a inclusão de prefixos. Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz. Neste caso, <xref:System.Windows.Data.Binding.XPath%2A> todas as referências de expressão devem incluir o prefixo mapeado pelo namespace apropriado. Para obter mais informações, consulte [Visão geral de vinculação de dados](../data/data-binding-overview.md).

Tecnicamente, `x:XData` pode ser usado como o <xref:System.Xml.Serialization.IXmlSerializable>conteúdo de qualquer propriedade do tipo. No <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> entanto, é a única implementação proeminente.

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Data.XmlDataProvider>
- [Visão geral da vinculação de dados](../data/data-binding-overview.md)
- [Extensão de marcação de associação](../../framework/wpf/advanced/binding-markup-extension.md)
