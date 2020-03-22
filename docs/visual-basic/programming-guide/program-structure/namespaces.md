---
title: Namespaces
ms.date: 07/20/2015
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
ms.openlocfilehash: ec892167f30a7ded739dc188ab4096cb3a5d154c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400669"
---
# <a name="namespaces-in-visual-basic"></a>Namespaces no Visual Basic
Namespaces organizam os objetos definidos em uma montagem. Os conjuntos podem conter vários namespaces, que por sua vez podem conter outros namespaces. Os namespaces impedem a ambiguidade e simplificam as referências ao usar grandes grupos de objetos, como bibliotecas de classe.  
  
 Por exemplo, o .NET <xref:System.Windows.Forms.ListBox> Framework define <xref:System.Windows.Forms?displayProperty=nameWithType> a classe no namespace. O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Evitando colisões de nomes  
 Os namespaces do .NET Framework abordam um problema às vezes chamado *de poluição de namespace,* no qual o desenvolvedor de uma biblioteca de classes é prejudicado pelo uso de nomes semelhantes em outra biblioteca. Esses conflitos com componentes existentes às vezes são chamados *de colisões de nomes*.  
  
 Por exemplo, se você criar `ListBox`uma nova classe chamada, você pode usá-la dentro do seu projeto sem qualificação. No entanto, se você quiser <xref:System.Windows.Forms.ListBox> usar a classe .NET Framework no mesmo projeto, você deve usar uma referência totalmente qualificada para tornar a referência única. Se a referência não for única, o Visual Basic produzirá um erro afirmando que o nome é ambíguo. O exemplo de código a seguir demonstra como declarar esses objetos:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 A ilustração a seguir mostra duas hierarquias `ListBox`de namespace, ambas contendo um objeto chamado :  
  
 ![Captura de tela que mostra duas hierarquias de namespace.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Por padrão, cada arquivo executável que você cria com o Visual Basic contém um namespace com o mesmo nome do seu projeto. Por exemplo, se você definir um `ListBoxProject`objeto dentro de um projeto chamado, o `ListBoxProject`arquivo executável ListBoxProject.exe contém um namespace chamado .  
  
 Vários conjuntos podem usar o mesmo namespace. Visual Basic os trata como um único conjunto de nomes. Por exemplo, você pode definir classes `SomeNameSpace` para um `Assemb1`namespace chamado em uma assembléia chamada `Assemb2`e definir classes adicionais para o mesmo namespace a partir de uma montagem chamada .  
  
## <a name="fully-qualified-names"></a>Nomes totalmente qualificados  
 Nomes totalmente qualificados são referências de objeto que são prefixadas com o nome do namespace no qual o objeto é definido. Você pode usar objetos definidos em outros projetos se criar uma referência à classe (escolhendo **Adicionar referência** no menu **Projeto)** e, em seguida, usar o nome totalmente qualificado para o objeto em seu código. O fragmento de código a seguir mostra como usar o nome totalmente qualificado para um objeto do namespace de outro projeto:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Nomes totalmente qualificados evitam conflitos de nomeação porque tornam possível que o compilador determine qual objeto está sendo usado. No entanto, os nomes em si podem ficar longos e complicados. Para contornar isso, você `Imports` pode usar a declaração para definir um *alias*— um nome abreviado que você pode usar no lugar de um nome totalmente qualificado. Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Se você `Imports` usar a declaração sem um alias, você pode usar todos os nomes nesse namespace sem qualificação, desde que sejam exclusivos do projeto. Se o `Imports` seu projeto contiver instruções para namespaces que contenham itens com o mesmo nome, você deve qualificar totalmente esse nome quando você usá-lo. Suponha, por exemplo, que `Imports` seu projeto contivesse as seguintes duas declarações:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Se você tentar `Class1` usá-lo sem qualificá-lo totalmente, o Visual Basic produzirá um erro afirmando que o nome `Class1` é ambíguo.  
  
## <a name="namespace-level-statements"></a>Declarações de nível de namespace  
 Dentro de um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces. Não é possível definir itens como propriedades, procedimentos, variáveis e eventos no nível de namespace. Esses itens devem ser declarados dentro de recipientes como módulos, estruturas ou classes.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Palavra-chave global em nomes totalmente qualificados  
 Se você definiu uma hierarquia aninhada de namespaces, o código dentro <xref:System?displayProperty=nameWithType> dessa hierarquia pode ser impedido de acessar o namespace do .NET Framework. O exemplo a seguir ilustra uma `SpecialSpace.System` hierarquia na <xref:System?displayProperty=nameWithType>qual o namespace bloqueia o acesso .  
  
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
  
 Como resultado, o compilador Visual Basic não <xref:System.Int32?displayProperty=nameWithType>consegue `SpecialSpace.System` resolver com `Int32`sucesso a referência a , porque não define . Você pode `Global` usar a palavra-chave para iniciar a cadeia de qualificação no nível mais externo da biblioteca de classes .NET Framework. Isso permite que <xref:System?displayProperty=nameWithType> você especifique o namespace ou qualquer outro namespace na biblioteca de classes. O exemplo a seguir ilustra isto.  
  
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
  
 Você pode `Global` usar para acessar outros namespaces <xref:Microsoft.VisualBasic?displayProperty=nameWithType>de nível raiz, como , e qualquer namespace associado ao seu projeto.  
  
## <a name="global-keyword-in-namespace-statements"></a>Palavra-chave global em declarações de namespace  
 Você também pode `Global` usar a palavra-chave em uma [declaração de namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Isso permite definir um namespace fora do namespace raiz do seu projeto.  
  
 Todos os namespaces do seu projeto são baseados no namespace raiz do projeto.  O Visual Studio atribui o nome do projeto como o namespace raiz padrão para todos os códigos do seu projeto. Por exemplo, se o `ConsoleApplication1`seu projeto for nomeado, `ConsoleApplication1`seus elementos de programação pertencem ao namespace . Se você `Namespace Magnetosphere`declarar , `Magnetosphere` as referências `ConsoleApplication1.Magnetosphere`ao projeto serão acessa .  
  
 Os exemplos a `Global` seguir usam a palavra-chave para declarar um namespace fora do namespace raiz para o projeto.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Em uma declaração `Global` de namespace, não pode ser aninhado em outro namespace.  
  
 Você pode usar a [página de aplicativo, designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) para visualizar e modificar o **namespace raiz** do projeto.  Para novos projetos, o **Root Namespace** é padrão para o nome do projeto. Para `Global` fazer com que o namespace de alto nível seja o espaço de nome de alto nível, você pode limpar a entrada **Root Namespace** para que a caixa esteja vazia. Limpar **o Espaço de Nome** `Global` raiz remove a necessidade da palavra-chave nas declarações de namespace.  
  
 Se `Namespace` uma declaração declarar um nome que também seja um namespace no .NET `Global` Framework, o namespace .NET Framework fica indisponível se a palavra-chave não for usada em um nome totalmente qualificado. Para habilitar o acesso a esse `Global` namespace do .NET `Global` Framework sem usar a palavra-chave, você pode incluir a palavra-chave na declaração. `Namespace`  
  
 O exemplo a `Global` seguir tem `System.Text` a palavra-chave na declaração namespace.  
  
 Se `Global` a palavra-chave não estivesse presente <xref:System.Text.StringBuilder> na declaração de `Global.System.Text.StringBuilder`namespace, não poderia ser acessada sem especificar . Para um `ConsoleApplication1`projeto chamado `System.Text` , `ConsoleApplication1.System.Text` as `Global` referências a acessar se a palavra-chave não fosse usada.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Referências e a Instrução Imports](references-and-the-imports-statement.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Escrevendo código em soluções do Office](/visualstudio/vsto/writing-code-in-office-solutions)
