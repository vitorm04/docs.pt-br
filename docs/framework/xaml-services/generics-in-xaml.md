---
title: Genéricos em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: faef74c57ac5ff9e3d4162accfc6552db55715bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="generics-in-xaml"></a>Genéricos em XAML
Os serviços do .NET Framework XAML conforme implementado no System. XAML fornece suporte ao uso de tipos genéricos do CLR. Esse suporte inclui especificando as restrições de genéricos como um argumento de tipo e impõe a restrição chamando apropriada `Add` método para casos de coleção genérica. Este tópico descreve os aspectos de usar e fazer referência a tipos genéricos em XAML.  
  
## <a name="xtypearguments"></a>X:TypeArguments  
 `x:TypeArguments` uma diretiva é definida pela linguagem XAML. Quando ele é usado como um membro de um tipo XAML que é apoiado por um tipo genérico, `x:TypeArguments` passa a restrição de tipo de argumentos genéricos para o construtor de backup. Para obter a sintaxe de referência que pertence aos serviços XAML do .NET Framework usar `x:TypeArguments`, que inclui exemplos de sintaxe, consulte [diretiva X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
 Porque `x:TypeArguments` usa uma cadeia de caracteres, e tem o apoio de conversor de tipo, normalmente, ela é declarada em uso como um atributo do XAML.  
  
 No fluxo do nó XAML, as informações são declarados por `x:TypeArguments` pode ser obtido <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> em um `StartObject` posição no fluxo do nó. O valor de retorno <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> é uma lista de <xref:System.Xaml.XamlType> valores. Determinar se um tipo XAML representa um tipo genérico pode ser feita por meio da chamada <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Regras e convenções de sintaxe para genéricos em XAML  
 Em XAML, um tipo genérico deve sempre ser representado como um genérico restrito; um genérico irrestrito nunca está presente no sistema de tipo XAML ou um fluxo do nó XAML e não pode ser representado na marcação XAML. Um genérico pode ser referenciado em sintaxe de atributo XAML, para casos em que é uma restrição de tipo aninhado de um genérico que está sendo referenciado por `x:TypeArguments`, ou para casos onde `x:Type` fornece uma referência de tipo CLR para um tipo genérico. Isso tem suporte por meio de <xref:System.Xaml.Schema.XamlTypeTypeConverter> classe definida por serviços XAML do .NET Framework.  
  
 O XAML atributo habilitado por do formulário de sintaxe <xref:System.Xaml.Schema.XamlTypeTypeConverter> altera o MSIL típico convenção de sintaxe CLR que usa o ângulo colchetes para tipos e as restrições de genéricos e, em vez disso, substitui o parênteses para o contêiner de restrição. Para obter um exemplo, consulte [diretiva X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Genéricos e recursos do XAML 2009  
 Se você usar o XAML 2009 em vez de mapeamento do CLR base tipos para obter tipos XAML para primitivos de linguagem comum, você pode usar [tipos internos XAML 2009](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md) como itens de informações em `x:TypeArguments`. Por exemplo, você pode declarar o seguinte (prefixo mapeamentos não mostrados, mas `x` é o namespace XAML linguagem XAML XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Suporte a genéricos no WPF e outras estruturas v 3.5  
 Para uso de 2006 XAML durante o direcionamento do WPF, especificamente [X:Class](../../../docs/framework/xaml-services/x-class-directive.md) também deve ser fornecido no mesmo elemento como `x:TypeArguments`, e esse elemento deve ser o elemento raiz em um documento XAML. O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Soluções alternativas para dar suporte a genéricos usos incluem a definição de uma extensão de marcação personalizadas que pode retornar tipos genéricos ou fornecendo um encapsulamento definição que deriva de um tipo genérico, mas simplifica a restrição genérica em sua própria definição de classe da classe.  
  
 No WPF e direcionamento [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar recursos XAML 2009 junto com `x:TypeArguments`, mas apenas para XAML livre (XAML não marcação-compilado). Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.  
  
 Fluxos de trabalho personalizados no Windows Workflow Foundation para [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] não oferecem suporte a uso XAML genérico.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva x:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md)  
 [Diretiva x:Class](../../../docs/framework/xaml-services/x-class-directive.md)  
 [Tipos inseridos para primitivos de linguagem XML comuns](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)
