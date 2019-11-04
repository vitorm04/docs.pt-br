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
ms.openlocfilehash: 8496e7c87cf7e6eea996ca7af4f288b7495c7661
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459906"
---
# <a name="xxdata-intrinsic-xaml-type"></a>Tipo intrínseco x:XData (XAML)
Habilita o posicionamento das ilhas de dados XML em uma produção XAML. Elementos XML dentro de `x:XData` não devem ser tratados por processadores XAML como se eles fossem uma parte do namespace XAML padrão atuante ou qualquer outro namespace XAML. `x:XData` pode conter XML bem formado arbitrário.  
  
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
|`elementDataRoot`|O elemento raiz único da ilha de dados embutida. Para os consumidores mais eventuales, o XML que não tem uma única raiz é considerado inválido. Em particular, uma única raiz será necessária se a `x:XData` for destinada como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.|  
|`[elementData]`|Opcional. XML que representa os dados XML. Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.|  
  
## <a name="remarks"></a>Comentários  
 Os elementos XML dentro de um objeto `x:XData` podem redeclarar todos os namespaces e prefixos possíveis de XMLDOM dentro dos dados.  
  
 O acesso programático a dados XML e o tipo de XAML intrínseco `x:XData` é possível em .NET Framework serviços XAML por meio da classe <xref:System.Windows.Markup.XData>.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 O objeto `x:XData` é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>ou, como alternativa, como o objeto filho da propriedade <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> (em XAML, isso normalmente é expresso em sintaxe de elemento de propriedade).  
  
 Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia). Isso é mais fácil para ilhas de dados simples porque as expressões de <xref:System.Windows.Data.Binding.XPath%2A> que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos. Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz. Nesse caso, todas as referências de expressão de <xref:System.Windows.Data.Binding.XPath%2A> devem incluir o prefixo mapeado para namespace apropriado. Para obter mais informações, consulte [Visão geral de vinculação de dados](../../desktop-wpf/data/data-binding-overview.md).  
  
 Tecnicamente, `x:XData` pode ser usada como o conteúdo de qualquer Propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>. No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a única implementação proeminente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.XmlDataProvider>
- [Visão geral da vinculação de dados](../../desktop-wpf/data/data-binding-overview.md)
- [Extensão de marcação de associação](../wpf/advanced/binding-markup-extension.md)
