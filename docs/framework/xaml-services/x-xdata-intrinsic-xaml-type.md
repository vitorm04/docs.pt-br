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
ms.openlocfilehash: c5f729837b9bb52ca7d232ca66b58e283a2bcefc
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053707"
---
# <a name="xxdata-intrinsic-xaml-type"></a>Tipo intrínseco x:XData (XAML)
Habilita o posicionamento das ilhas de dados XML em uma produção XAML. Elementos XML dentro `x:XData` não devem ser tratados por processadores XAML como se eles fossem uma parte do namespace XAML padrão agindo ou qualquer outro namespace XAML. `x:XData`pode conter XML bem formado arbitrário.  
  
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
|`elementDataRoot`|O elemento raiz único da ilha de dados embutida. Para os consumidores mais eventuales, o XML que não tem uma única raiz é considerado inválido. Em particular, uma única raiz é necessária se o `x:XData` se destina como uma fonte de dados XML para WPF ou muitas outras tecnologias que usam fontes XML para vinculação de dados.|  
|`[elementData]`|Opcional. XML que representa os dados XML. Qualquer número de elementos pode ser contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; no entanto, as regras gerais do XML se aplicam.|  
  
## <a name="remarks"></a>Comentários  
 Os elementos XML dentro de `x:XData` um objeto podem redeclarar todos os namespaces e prefixos possíveis de XMLDOM dentro dos dados.  
  
 O acesso programático a dados XML `x:XData` e o tipo intrínseco de XAML é possível em .NET Framework serviços <xref:System.Windows.Markup.XData> XAML por meio da classe.  
  
## <a name="wpf-usage-notes"></a>Observações de uso do WPF  
 O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>ou, como alternativa, como <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> o objeto filho da propriedade (em XAML, normalmente é expresso em sintaxe de elemento de propriedade).  
  
 Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia). Isso é mais fácil para ilhas de dados simples porque <xref:System.Windows.Data.Binding.XPath%2A> as expressões que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos. Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz. Nesse caso, todas as <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo mapeado para namespace apropriado. Para obter mais informações, consulte [Visão geral de vinculação de dados](../wpf/data/data-binding-overview.md).  
  
 Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer Propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>. No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a única implementação proeminente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.XmlDataProvider>
- [Visão geral da vinculação de dados](../wpf/data/data-binding-overview.md)
- [Extensão de marcação de associação](../wpf/advanced/binding-markup-extension.md)
