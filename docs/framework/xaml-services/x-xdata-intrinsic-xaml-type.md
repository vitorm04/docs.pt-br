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
ms.openlocfilehash: c8044bc341ded6ef7b03bbdf701e724654460d54
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125153"
---
# <a name="xxdata-intrinsic-xaml-type"></a>Tipo intrínseco x:XData (XAML)
Habilita o posicionamento de ilhas de dados XML dentro de uma produção de XAML. Elementos XML em `x:XData` não deve ser tratada pelos processadores XAML, como se eles são uma parte do namespace XAML padrão atuando ou qualquer outro namespace XAML. `x:XData` pode conter XML bem formado arbitrário.  
  
## <a name="xaml-object-element-usage"></a>Uso de elemento Object do XAML  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|`elementDataRoot`|O elemento de raiz única da ilha de dados incluídos. Para a maioria dos consumidores eventual, XML que não tem uma única raiz é considerado inválido. Em particular, uma única raiz será necessária se o `x:XData` destina-se como uma fonte de dados XML para o WPF ou muitas outras tecnologias que usam fontes de XML para vinculação de dados.|  
|`[elementData]`|Opcional. XML que representa os dados XML. Qualquer número de elementos pode estar contido como dados de elemento e elementos aninhados podem estar contidos em outros elementos; No entanto, se aplicam as regras gerais de XML.|  
  
## <a name="remarks"></a>Comentários  
 Os elementos XML dentro de um `x:XData` objeto pode declarar novamente todos os possíveis namespaces e prefixos do XMLDOM recipiente dentro dos dados.  
  
 Acesso programático aos dados XML e o `x:XData` tipo intrínseco do XAML é possível em serviços de XAML do .NET Framework por meio de <xref:System.Windows.Markup.XData> classe.  
  
## <a name="wpf-usage-notes"></a>Notas de uso do WPF  
 O `x:XData` objeto é usado principalmente como um objeto filho de um <xref:System.Windows.Data.XmlDataProvider>, ou como alternativa, como o objeto filho do <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriedade (no XAML, isso é normalmente expressa na sintaxe de elemento de propriedade).  
  
 Os dados normalmente devem redefinir o namespace XML base dentro da ilha de dados para ser um novo namespace XML padrão (definido como uma cadeia de caracteres vazia). Isso é mais fácil para ilhas de dados simples, porque o <xref:System.Windows.Data.Binding.XPath%2A> expressões que são usadas para referenciar e associar aos dados podem evitar a inclusão de prefixos. Ilhas de dados mais complexas podem definir vários prefixos para os dados e usar um prefixo específico para o namespace XML na raiz. Nesse caso, todos os <xref:System.Windows.Data.Binding.XPath%2A> referências de expressão devem incluir o prefixo de namespace mapeado apropriado. Para obter mais informações, consulte [Visão geral de vinculação de dados](../wpf/data/data-binding-overview.md).  
  
 Tecnicamente, `x:XData` pode ser usado como o conteúdo de qualquer propriedade do tipo <xref:System.Xml.Serialization.IXmlSerializable>. No entanto, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> é a implementação apenas proeminente.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Data.XmlDataProvider>
- [Visão geral da vinculação de dados](../wpf/data/data-binding-overview.md)
- [Extensão de marcação de associação](../wpf/advanced/binding-markup-extension.md)
