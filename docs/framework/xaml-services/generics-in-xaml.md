---
title: Genéricos em XAML
ms.date: 03/30/2017
helpviewer_keywords:
- generics [XAML Services]
ms.assetid: 835bfed7-585c-4216-ae67-b674edab8b92
ms.openlocfilehash: 219c710e8552ae3291c2b144c6048f4ff6710540
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58048912"
---
# <a name="generics-in-xaml"></a>Genéricos em XAML
Os serviços do .NET Framework XAML como implementado no System. XAML oferece suporte para uso de tipos genéricos do CLR. Esse suporte inclui especificando as restrições de genéricos como um argumento de tipo e impõe a restrição de chamando apropriado `Add` método para casos de coleção genérica. Este tópico descreve aspectos de usar e fazer referência a tipos genéricos em XAML.  
  
## <a name="xtypearguments"></a>x:TypeArguments  
 `x:TypeArguments` uma diretiva é definida pela linguagem XAML. Quando ele é usado como um membro de um tipo XAML que é apoiado por um tipo genérico, `x:TypeArguments` passa a restrição de tipo argumentos de genérico para o construtor de backup. Para obter a sintaxe de referência que pertencem aos serviços de XAML do .NET Framework, use de `x:TypeArguments`, que inclui exemplos de sintaxe, consulte [diretiva X:TypeArguments](x-typearguments-directive.md).  
  
 Porque `x:TypeArguments` usa uma cadeia de caracteres e tem o apoio de conversor de tipo, ele normalmente é declarado no uso XAML como um atributo.  
  
 No fluxo de nó XAML, as informações são declarados por `x:TypeArguments` pode ser obtido <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> em um `StartObject` posição no fluxo de nó. O valor de retorno <xref:System.Xaml.XamlType.TypeArguments%2A?displayProperty=nameWithType> é uma lista de <xref:System.Xaml.XamlType> valores. Determinação de se um tipo XAML representa um tipo genérico pode ser feita por meio da chamada <xref:System.Xaml.XamlType.IsGeneric%2A?displayProperty=nameWithType>.  
  
## <a name="rules-and-syntax-conventions-for-generics-in-xaml"></a>Regras e convenções de sintaxe para genéricos em XAML  
 No XAML, um tipo genérico sempre deve ser representado como um elemento genérico restrito; um genérico irrestrito nunca está presente no sistema de tipos XAML ou um fluxo do nó XAML e não pode ser representado na marcação XAML. Um genérico pode ser referenciado em sintaxe de atributo XAML, para casos em que é uma restrição de tipo aninhado de um genérico que está sendo referenciado por `x:TypeArguments`, ou para casos em que `x:Type` fornece uma referência de tipo CLR para um tipo genérico. Isso é compatível com o <xref:System.Xaml.Schema.XamlTypeTypeConverter> classe definida pelos serviços de XAML do .NET Framework.  
  
 O XAML habilitado do formulário de sintaxe de atributo <xref:System.Xaml.Schema.XamlTypeTypeConverter> altera o típico MSIL / convenção de sintaxe CLR que usa o ângulo colchetes para tipos e as restrições de genéricos e, em vez disso substitui pelos parênteses para o contêiner de restrição. Por exemplo, consulte [diretiva X:TypeArguments](x-typearguments-directive.md).  
  
## <a name="generics-and-xaml-2009-features"></a>Genéricos e recursos do XAML 2009  
 Se você usar o XAML 2009 em vez de mapeamento do CLR tipos para obter tipos XAML para primitivos de linguagem comuns de base, você pode usar [tipos internos do XAML 2009](built-in-types-for-common-xaml-language-primitives.md) como itens de informações em `x:TypeArguments`. Por exemplo, você poderia declarar o seguinte (prefixo mapeamentos não mostrados, mas `x` é o namespace XAML de linguagem XAML para XAML 2009):  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
## <a name="generics-support-in-wpf-and-other-v35-frameworks"></a>Suporte a genéricos no WPF e outros Frameworks v 3.5  
 Para o uso do XAML 2006 ao direcionar o WPF, especificamente [X:Class](x-class-directive.md) também deve ser fornecido no mesmo elemento que `x:TypeArguments`, e esse elemento deve ser o elemento raiz em um documento XAML. O elemento raiz deve mapear para um tipo genérico com pelo menos um argumento de tipo. Um exemplo é <xref:System.Windows.Navigation.PageFunction%601>.  
  
 Possíveis soluções alternativas para dar suporte a usos genéricos incluem definir uma extensão de marcação personalizada que pode retornar tipos genéricos ou fornecendo um encapsulamento definição que deriva de um tipo genérico, mas que nivela a restrição genérica em sua própria definição de classe da classe.  
  
 No WPF e o direcionamento [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar recursos do XAML 2009 junto com `x:TypeArguments`, mas somente para XAML flexível (XAML não é compilado por marcação). Compilado por marcação XAML para WPF e o formato BAML de XAML têm suporte no momento, as palavras-chave do XAML 2009 e os recursos.  
  
 Fluxos de trabalho personalizados no Windows Workflow Foundation para [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] não dão suporte a uso genérico de XAML.  
  
## <a name="see-also"></a>Consulte também
- [Diretiva x:TypeArguments](x-typearguments-directive.md)
- [Diretiva x:Class](x-class-directive.md)
- [Tipos inseridos para primitivos de linguagem XML comuns](built-in-types-for-common-xaml-language-primitives.md)
