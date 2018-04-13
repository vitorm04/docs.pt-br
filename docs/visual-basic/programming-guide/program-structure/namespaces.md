---
title: Namespaces no Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.global
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- name collisions
- Global keyword [Visual Basic]
- namespace pollution
- names [Visual Basic], avoiding conflicts
- naming conflicts [Visual Basic], namespaces
- namespaces [Visual Basic], assemblies
- Visual Basic code, namespaces
- fully qualified names [Visual Basic]
- naming conventions [Visual Basic], naming conflicts
- namespaces
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c18d0a9abb1d8b9e3e22f3b81bf605fb8ed75cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="namespaces-in-visual-basic"></a>Namespaces no Visual Basic
Namespaces organizar os objetos definidos em um assembly. Os assemblies podem conter vários namespaces, que por sua vez pode conter outros namespaces. Namespaces evitar a ambiguidade e simplificar as referências ao usar grandes grupos de objetos, como bibliotecas de classe.  
  
 Por exemplo, o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] define o <xref:System.Windows.Forms.ListBox> classe no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace. O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## <a name="avoiding-name-collisions"></a>Evitando conflitos de nome  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]namespaces solucionar um problema que às vezes chamado de *poluição de namespace*, em que o desenvolvedor de uma biblioteca de classe é reduzido pelo uso de nomes semelhantes em outra biblioteca. Esses conflitos com os componentes existentes são chamados de *nome colisões*.  
  
 Por exemplo, se você criar uma nova classe chamada `ListBox`, você pode usá-lo em seu projeto sem qualificação. No entanto, se você quiser usar o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.Windows.Forms.ListBox> classe no mesmo projeto, você deve usar uma referência totalmente qualificada para tornar a referência exclusiva. Se a referência não for exclusiva, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] produz um erro informando que o nome é ambíguo. O exemplo de código a seguir demonstra como declarar esses objetos:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 A ilustração a seguir mostra duas hierarquias de namespace, ambos os que contém um objeto chamado `ListBox`.  
  
 ![Hierarquia de Namespace](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Por padrão, cada arquivo executável que você criar com [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] contém um namespace com o mesmo nome de seu projeto. Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject.exe contém um namespace chamado `ListBoxProject`.  
  
 Vários assemblies podem usar o mesmo namespace. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]trata-los como um único conjunto de nomes. Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly nomeado `Assemb1`e definir classes adicionais para o mesmo namespace de um assembly chamado `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Nomes totalmente qualificados  
 Nomes totalmente qualificados são referências a objetos que são prefixadas com o nome do namespace no qual o objeto é definido. Você pode usar objetos definidos em outros projetos, se você criar uma referência à classe (escolhendo **adicionar referência** do **projeto** menu) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código. O fragmento de código a seguir mostra como usar o nome totalmente qualificado de um objeto de namespace outro projeto do:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Nomes totalmente qualificados impedem a nomeação entra em conflito porque eles tornam possível para o compilador determinar qual objeto está sendo usado. No entanto, os nomes podem obter longas e complicadas. Para contornar esse problema, você pode usar o `Imports` instrução para definir um *alias*— um nome abreviado, você pode usar no lugar do nome totalmente qualificado. Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Se você usar o `Imports` instrução sem um alias, você pode usar todos os nomes em que o namespace sem qualificação, fornecidas sejam exclusivas para o projeto. Se o seu projeto contém `Imports` instruções para os namespaces que contêm itens com o mesmo nome, você deve qualificar totalmente esse nome quando você usá-lo. Suponha que, por exemplo, seu projeto continha os dois seguintes `Imports` instruções:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Se você tentar usar `Class1` sem qualificar totalmente, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] produz um erro informando que o nome `Class1` é ambíguo.  
  
## <a name="namespace-level-statements"></a>Instruções de nível de Namespace  
 Dentro de um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces. Não é possível definir itens como propriedades, procedimentos, variáveis e eventos em nível de namespace. Esses itens devem ser declarados em contêineres, como classes, estruturas ou módulos.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Palavra-chave global em nomes totalmente qualificados  
 Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia poderão ser impedido de acessar o <xref:System?displayProperty=nameWithType> namespace do .NET Framework. O exemplo a seguir ilustra uma hierarquia na qual o `SpecialSpace.System` namespace bloqueia o acesso à <xref:System?displayProperty=nameWithType>.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As System.Int32  
                Dim n As System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Como resultado, o compilador do Visual Basic com êxito não é possível resolver a referência ao <xref:System.Int32?displayProperty=nameWithType>, pois `SpecialSpace.System` não define `Int32`. Você pode usar o `Global` palavra-chave para iniciar a cadeia de qualificação no nível mais externo da biblioteca de classes do .NET Framework. Isso permite que você especifique o <xref:System?displayProperty=nameWithType> namespace ou qualquer outro namespace na biblioteca de classes. O exemplo a seguir ilustra essa situação.  
  
```vb  
Namespace SpecialSpace  
    Namespace System  
        Class abc  
            Function getValue() As Global.System.Int32  
                Dim n As Global.System.Int32  
                Return n  
            End Function  
        End Class  
    End Namespace  
End Namespace  
```  
  
 Você pode usar `Global` para acessar outros namespaces no nível raiz, como <xref:Microsoft.VisualBasic?displayProperty=nameWithType>e qualquer namespace associado ao seu projeto.  
  
## <a name="global-keyword-in-namespace-statements"></a>Palavra-chave em instruções de Namespace global  
 Você também pode usar o `Global` palavra-chave em um [declaração de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Isso permite definir um namespace do namespace raiz do projeto.  
  
 Todos os namespaces no seu projeto baseiam-se no namespace raiz do projeto.  Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto. Por exemplo, se seu projeto for chamado `ConsoleApplication1`, seus elementos de programação pertencem ao namespace `ConsoleApplication1`. Se você declarar `Namespace Magnetosphere`, as referências a `Magnetosphere` no projeto terão acesso `ConsoleApplication1.Magnetosphere`.  
  
 Os exemplos a seguir usam o `Global` palavra-chave para declarar um namespace do namespace raiz do projeto.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Em uma declaração de namespace, `Global` não pode ser aninhado em outro namespace.  
  
 Você pode usar o [página de aplicativo, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **Namespace raiz** do projeto.  Para novos projetos, o **Namespace raiz** padrão é o nome do projeto. Para fazer com que `Global` para ser o namespace de nível superior, você pode limpar o **Namespace raiz** entrada para que a caixa estiver vazia. Limpando **Namespace raiz** elimina a necessidade do `Global` palavra-chave em declarações de namespace.  
  
 Se um `Namespace` instrução declara um nome que também é um namespace do .NET Framework, o namespace do .NET Framework se torna indisponível se o `Global` palavra-chave não é usado em um nome totalmente qualificado. Para habilitar o acesso a esse namespace do .NET Framework sem usar o `Global` palavra-chave, você pode incluir o `Global` palavra-chave no `Namespace` instrução.  
  
 O exemplo a seguir tem o `Global` palavra-chave no `System.Text` declaração de namespace.  
  
 Se o `Global` palavra-chave não estava presente na declaração de namespace, <xref:System.Text.StringBuilder> não pôde ser acessado sem especificar `Global.System.Text.StringBuilder`. Para um projeto chamado `ConsoleApplication1`, as referências a `System.Text` acessaria `ConsoleApplication1.System.Text` se o `Global` palavra-chave não foi usado.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms?displayProperty=nameWithType>  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Como criar e usar assemblies usando a linha de comando](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Referências e a Instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Escrevendo código em soluções do Office](https://msdn.microsoft.com/library/bb608596)
