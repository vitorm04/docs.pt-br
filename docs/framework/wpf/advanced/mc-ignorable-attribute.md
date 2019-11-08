---
title: Atributo mc:Ignorable
ms.date: 03/30/2017
helpviewer_keywords:
- mc XML namespace prefix [WPF]
- mc:Ignorable attribute
- XML [WPF], mc namespace prefix
- XAML [WPF], mc:Ignorable attribute
- mc:ProcessContent attribute
- XAML [WPF], mc:ProcessContent attribute
ms.assetid: acd9a6ef-b7ca-4146-abb6-60f3b366e9ec
ms.openlocfilehash: e14ab0ebc7d44e2792307b16c7c0581ff7a71bc6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740827"
---
# <a name="mcignorable-attribute"></a>Atributo mc:Ignorable
Especifica quais prefixos de namespace XML encontrados em um arquivo de marcação podem ser ignorados por um processador de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. O atributo `mc:Ignorable` dá suporte à compatibilidade de marcação para o mapeamento de namespace personalizado e para controle de versão de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
## <a name="xaml-attribute-usage-single-prefix"></a>Uso do atributo XAML (prefixo único)  
  
```xaml  
<object  
  xmlns:ignorablePrefix="ignorableUri"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-attribute-usage-two-prefixes"></a>Uso do atributo XAML (dois prefixos)  
  
```xaml  
<object  
  xmlns:ignorablePrefix1="ignorableUri"  
  xmlns:ignorablePrefix2="ignorableUri2"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="ignorablePrefix1 ignorablePrefix2"...>  
    <ignorablePrefix1:ThisElementCanBeIgnored/>  
</object>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*ignorablePrefix, ignorablePrefix1, etc.*|Qualquer cadeia de caracteres de prefixo é válida, conforme a especificação de XML 1.0.|  
|*ignorableUri*|Qualquer URI válido para designar um namespace, conforme a especificação XML 1.0.|  
|*ThisElementCanBeIgnored*|Um elemento que poderá ser ignorado por implementações do processador [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], se o tipo subjacente não puder ser resolvido.|  
  
## <a name="remarks"></a>Comentários  
 O prefixo de namespace XML `mc` é a Convenção de prefixo recomendada a ser usada ao mapear o `http://schemas.openxmlformats.org/markup-compatibility/2006`namespace de compatibilidade de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Elementos ou atributos em que a parte do prefixo do nome do elemento é identificado como `mc:Ignorable` não gerarão erros quando processados por um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Se esse atributo não puder ser resolvido para um tipo subjacente ou constructo de programação, esse elemento será ignorado. No entanto, observe que elementos ignorados ainda podem gerar erros de análise adicionais para requisitos de elementos adicionais que são efeitos colaterais do elemento não estar sendo processado. Por exemplo, um modelo de conteúdo do elemento específico pode requerer exatamente um elemento filho, porém, se o elemento filho especificado estava em um prefixo `mc:Ignorable` e o elemento filho especificado não pôde ser resolvido para um tipo, então o processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pode gerar um erro.  
  
 `mc:Ignorable` aplica-se somente a mapeamentos de namespace para cadeias de caracteres de identificador. `mc:Ignorable` não se aplica a mapeamentos de namespace em assemblies, que especificam um namespace CLR e um assembly (ou, por padrão, o executável atual como o assembly).  
  
 Se você estiver implementando um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], a implementação do processador não deverá gerar erros de análise ou de processamento na resolução de tipos para qualquer elemento ou atributo qualificado por um prefixo identificado como `mc:Ignorable`. Contudo, a implementação do processador pode, ainda assim, gerar exceções que são um resultado secundário da falha de um elemento ao carregar ou ser processado, como no exemplo de filho único fornecido anteriormente.  
  
 Por padrão, um processador [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ignorará o conteúdo dentro de um elemento ignorado. No entanto, você pode especificar um atributo adicional, [Atributo mc:ProcessContent](mc-processcontent-attribute.md), para exigir o processamento de conteúdo contínuo dentro de um elemento ignorado pelo próximo elemento pai disponível.  
  
 Vários prefixos podem ser especificados no atributo, usando um ou mais caracteres de espaço em branco como separador, por exemplo: `mc:Ignorable="ignore1 ignore2"`.  

 O namespace `http://schemas.openxmlformats.org/markup-compatibility/2006` define outros elementos e atributos que não estão documentados nessa área do SDK. Para obter mais informações, consulte [Especificação de compatibilidade de marcação XML](/office/open-xml/introduction-to-markup-compatibility#markup-compatibility-in-the-open-xml-file-formats-specification).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Markup.XamlReader>
- [Atributo PresentationOptions:Freeze](presentationoptions-freeze-attribute.md)
- [Visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [Documentos no WPF](documents-in-wpf.md)
