---
title: "Namespaces no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.global"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "assemblies [Visual Basic], namespaces"
  - "conflitos de nome"
  - "palavra-chave Global [Visual Basic]"
  - "poluição de namespace"
  - "nomes, evitando conflitos"
  - "conflitos de nomenclatura, namespaces"
  - "namespaces, assemblies"
  - "Código do Visual Basic, namespaces"
  - "nomes totalmente qualificados"
  - "convenções de nomenclatura, conflitos de nomenclatura"
  - "namespaces"
ms.assetid: cffac744-ab8c-4f1f-ba50-732c22ab4b88
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Namespaces no Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Os namespaces organizam os objetos definidos em um assembly. Os assemblies podem conter vários namespaces, que por sua vez pode conter outros namespaces. Namespaces evitar a ambiguidade e simplificar as referências ao usar grupos grandes de objetos, como bibliotecas de classes.  
  
 Por exemplo, o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] define o <xref:System.Windows.Forms.ListBox> classe o <xref:System.Windows.Forms?displayProperty=fullName> namespace. O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:  
  
 [!code-vb[VbVbalrApplication#6](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_1.vb)]  
  
## Evitando conflitos de nome  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] namespaces resolver um problema chamado às vezes *poluição de namespace*, em que o desenvolvedor de uma biblioteca de classe é violado pelo uso de nomes semelhantes em outra biblioteca. Esses conflitos com os componentes existentes são chamados *conflitos de nome*.  
  
 Por exemplo, se você criar uma nova classe chamada `ListBox`, você pode usá\-lo em seu projeto sem qualificação. No entanto, se você quiser usar o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.Windows.Forms.ListBox> classe no mesmo projeto, você deve usar uma referência totalmente qualificada para fazer a referência exclusiva.  Se a referência não for exclusiva, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produz um erro informando que o nome é ambíguo. O exemplo de código a seguir demonstra como declarar esses objetos:  
  
 [!code-vb[VbVbalrApplication#7](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_2.vb)]  
  
 A ilustração a seguir mostra duas hierarquias de namespace, ambos os que contém um objeto chamado `ListBox`.  
  
 ![Namespace Hierarchy](../../../visual-basic/programming-guide/program-structure/media/vanamespacehierarchy.gif "vaNamespaceHierarchy")  
  
 Por padrão, cada arquivo executável que você criar com [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] contém um namespace com o mesmo nome do seu projeto. Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject.exe contém um namespace chamado `ListBoxProject`.  
  
 Vários assemblies podem usar o mesmo namespace.[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] trata\-os como um único conjunto de nomes. Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly denominado `Assemb1`, e definir classes adicionais para o mesmo namespace de um assembly denominado `Assemb2`.  
  
## Nomes totalmente qualificados  
 Nomes totalmente qualificados são referências de objeto que são prefixadas com o nome do namespace no qual o objeto é definido. Você pode usar objetos definidos em outros projetos, se você criar uma referência à classe \(escolhendo **Adicionar referência** do **projeto** menu\) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código. O fragmento de código a seguir mostra como usar o nome totalmente qualificado de um objeto de namespace outro projeto do:  
  
 [!code-vb[VbVbalrApplication#8](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_3.vb)]  
  
 Nomes totalmente qualificados impedem a nomeação entra em conflito porque eles possibilitam que o compilador determinar qual objeto está sendo usado. No entanto, os nomes podem obter longo e complicado. Para contornar esse problema, você pode usar o `Imports` instrução para definir um *alias*— um nome abreviado que você pode usar no lugar de um nome totalmente qualificado. Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.  
  
 [!code-vb[VbVbalrApplication#9](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_4.vb)]  
  
 [!code-vb[VbVbalrApplication#10](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_5.vb)]  
  
 Se você usar o `Imports` instrução sem um alias, você pode usar todos os nomes que namespace sem qualificação, fornecidas sejam exclusivas para o projeto. Se seu projeto contém `Imports` instruções para os namespaces que contêm itens com o mesmo nome, você deve qualificar totalmente esse nome quando você usá\-lo. Suponha, por exemplo, seu projeto contidos nas próximas duas `Imports` instruções:  
  
 [!code-vb[VbVbalrApplication#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_6.vb)]  
  
 Se você tentar usar `Class1` sem qualificar totalmente, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] produz um erro informando que o nome `Class1` é ambíguo.  
  
## Declarações de nível de namespace  
 Dentro de um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces. Não é possível definir itens como propriedades, procedimentos, variáveis e eventos no nível de namespace. Esses itens devem ser declarados dentro de contêineres, como módulos, classes ou estruturas.  
  
## Palavra\-chave global em nomes totalmente qualificados  
 Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia pode ser impedido de acessar o <xref:System?displayProperty=fullName> namespace do .NET Framework. O exemplo a seguir ilustra uma hierarquia na qual o `SpecialSpace.System` namespace bloqueia o acesso à <xref:System?displayProperty=fullName>.  
  
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
  
 Como resultado, o compilador do Visual Basic não pode resolver com êxito a referência à <xref:System.Int32?displayProperty=fullName>, pois `SpecialSpace.System` não define `Int32`. Você pode usar o `Global` palavra\-chave para iniciar a cadeia de qualificação no nível mais externo de biblioteca de classes .NET Framework. Isso permite que você especifique o <xref:System?displayProperty=fullName> namespace ou qualquer outro namespace na biblioteca de classes. O exemplo a seguir ilustra isso.  
  
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
  
 Você pode usar `Global` para acessar outros namespaces no nível da raiz, como <xref:Microsoft.VisualBasic?displayProperty=fullName>, e qualquer namespace associado ao projeto.  
  
## Palavra\-chave nas declarações de Namespace global  
 Você também pode usar o `Global` palavra\-chave em um [Instrução Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Isso permite definir um namespace fora do namespace raiz do projeto.  
  
 Todos os namespaces em seu projeto são baseados no namespace raiz do projeto.  Visual Studio atribui o nome do projeto como o namespace de raiz padrão para todo o código em seu projeto. Por exemplo, se seu projeto for chamado `ConsoleApplication1`, seus elementos de programação pertencem ao namespace `ConsoleApplication1`. Se você declarar `Namespace Magnetosphere`, as referências a `Magnetosphere` no projeto irá acessar `ConsoleApplication1.Magnetosphere`.  
  
 Os exemplos a seguir usam o `Global` palavra\-chave para declarar um namespace fora do namespace raiz do projeto.  
  
 [!code-vb[VbVbalrApplication#22](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_7.vb)]  
  
 Em uma declaração de namespace, `Global` não pode ser aninhado em outro namespace.  
  
 Você pode usar o [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **Namespace raiz** do projeto.  Para novos projetos, o **Namespace raiz** assume como padrão o nome do projeto. Para fazer com que `Global` para ser o namespace de nível superior, você pode limpar o **Namespace raiz** entrada para que a caixa estiver vazia. Limpando **Namespace raiz** elimina a necessidade do `Global` palavra\-chave em declarações de namespace.  
  
 Se um `Namespace` instrução declara um nome que também é um namespace do .NET Framework, o namespace do .NET Framework se torna indisponível se o `Global` palavra\-chave não é usada em um nome totalmente qualificado. Para habilitar o acesso a esse namespace do .NET Framework sem usar o `Global` palavra\-chave, você pode incluir o `Global` palavra\-chave no `Namespace` instrução.  
  
 O exemplo a seguir tem o `Global` palavra\-chave no `System.Text` declaração de namespace.  
  
 Se o `Global` palavra\-chave não estava presente na declaração de namespace, <xref:System.Text.StringBuilder> não pôde ser acessado sem especificar `Global.System.Text.StringBuilder`. Para um projeto chamado `ConsoleApplication1`, as referências a `System.Text` acessaria `ConsoleApplication1.System.Text` se o `Global` palavra\-chave não foi usado.  
  
 [!code-vb[VbVbalrApplication#21](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/namespaces_8.vb)]  
  
## Consulte também  
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms?displayProperty=fullName>   
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como criar e usar assemblies usando a linha de comando](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Escrevendo código em soluções do Office](/office-dev/office-dev/writing-code-in-office-solutions)