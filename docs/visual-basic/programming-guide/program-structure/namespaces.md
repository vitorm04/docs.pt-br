---
title: '{1&gt;Namespaces&lt;1}'
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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347324"
---
# <a name="namespaces-in-visual-basic"></a>Namespaces no Visual Basic
Os namespaces organizam os objetos definidos em um assembly. Os assemblies podem conter vários namespaces, que, por sua vez, podem conter outros namespaces. Os namespaces impedem ambigüidade e simplificam referências ao usar grandes grupos de objetos, como bibliotecas de classes.  
  
 Por exemplo, o .NET Framework define a classe <xref:System.Windows.Forms.ListBox> no namespace <xref:System.Windows.Forms?displayProperty=nameWithType>. O fragmento de código a seguir mostra como declarar uma variável usando o nome totalmente qualificado para esta classe:  
  
 [!code-vb[VbVbalrApplication#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#6)]  
  
## <a name="avoiding-name-collisions"></a>Evitando colisões de nome  
 Os namespaces .NET Framework resolvem um problema às vezes chamado de *poluição de namespace*, em que o desenvolvedor de uma biblioteca de classes é dificultado pelo uso de nomes semelhantes em outra biblioteca. Esses conflitos com os componentes existentes às vezes são chamados de *colisões de nome*.  
  
 Por exemplo, se você criar uma nova classe chamada `ListBox`, poderá usá-la dentro de seu projeto sem qualificação. No entanto, se você quiser usar a classe .NET Framework <xref:System.Windows.Forms.ListBox> no mesmo projeto, deverá usar uma referência totalmente qualificada para tornar a referência exclusiva. Se a referência não for exclusiva, Visual Basic produzirá um erro informando que o nome é ambíguo. O exemplo de código a seguir demonstra como declarar esses objetos:  
  
 [!code-vb[VbVbalrApplication#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#7)]  
  
 A ilustração a seguir mostra duas hierarquias de namespace, ambas contendo um objeto chamado `ListBox`:  
  
 ![Captura de tela que mostra duas hierarquias de namespace.](./media/namespaces/visual-basic-namespace-hierarchy.gif)  
  
 Por padrão, cada arquivo executável que você cria com Visual Basic contém um namespace com o mesmo nome do seu projeto. Por exemplo, se você definir um objeto em um projeto chamado `ListBoxProject`, o arquivo executável ListBoxProject. exe conterá um namespace chamado `ListBoxProject`.  
  
 Vários assemblies podem usar o mesmo namespace. Visual Basic os trata como um único conjunto de nomes. Por exemplo, você pode definir classes para um namespace chamado `SomeNameSpace` em um assembly chamado `Assemb1`e definir classes adicionais para o mesmo namespace de um assembly chamado `Assemb2`.  
  
## <a name="fully-qualified-names"></a>Nomes totalmente qualificados  
 Nomes totalmente qualificados são referências de objeto que são prefixadas com o nome do namespace no qual o objeto é definido. Você pode usar objetos definidos em outros projetos se criar uma referência à classe (escolhendo **Adicionar referência** no menu **projeto** ) e, em seguida, usar o nome totalmente qualificado para o objeto em seu código. O fragmento de código a seguir mostra como usar o nome totalmente qualificado para um objeto do namespace de outro projeto:  
  
 [!code-vb[VbVbalrApplication#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#8)]  
  
 Nomes totalmente qualificados impedem conflitos de nomenclatura porque possibilitam que o compilador determine qual objeto está sendo usado. No entanto, os próprios nomes podem ser longos e complicados. Para contornar isso, você pode usar a instrução `Imports` para definir um *alias*— um nome abreviado que você pode usar no lugar de um nome totalmente qualificado. Por exemplo, o exemplo de código a seguir cria aliases para dois nomes totalmente qualificados e usa esses aliases para definir dois objetos.  
  
 [!code-vb[VbVbalrApplication#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#9)]  
  
 [!code-vb[VbVbalrApplication#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#10)]  
  
 Se você usar a instrução `Imports` sem um alias, poderá usar todos os nomes nesse namespace sem qualificação, desde que eles sejam exclusivos ao projeto. Se o seu projeto contiver instruções `Imports` para namespaces que contêm itens com o mesmo nome, você deverá qualificar totalmente esse nome ao usá-lo. Suponha, por exemplo, que o projeto contivesse as duas instruções `Imports` a seguir:  
  
 [!code-vb[VbVbalrApplication#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/Class1.vb#11)]  
  
 Se você tentar usar `Class1` sem qualificar-se totalmente, Visual Basic produzirá um erro informando que o nome `Class1` é ambíguo.  
  
## <a name="namespace-level-statements"></a>Instruções de nível de namespace  
 Em um namespace, você pode definir itens como módulos, interfaces, classes, delegados, enumerações, estruturas e outros namespaces. Você não pode definir itens como propriedades, procedimentos, variáveis e eventos no nível de namespace. Esses itens devem ser declarados em contêineres, como módulos, estruturas ou classes.  
  
## <a name="global-keyword-in-fully-qualified-names"></a>Palavra-chave global em nomes totalmente qualificados  
 Se você tiver definido uma hierarquia aninhada de namespaces, o código dentro dessa hierarquia poderá ser impedido de acessar o namespace <xref:System?displayProperty=nameWithType> do .NET Framework. O exemplo a seguir ilustra uma hierarquia na qual o namespace `SpecialSpace.System` bloqueia o acesso a <xref:System?displayProperty=nameWithType>.  
  
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
  
 Como resultado, o compilador Visual Basic não pode resolver com êxito a referência a <xref:System.Int32?displayProperty=nameWithType>, porque `SpecialSpace.System` não define `Int32`. Você pode usar a palavra-chave `Global` para iniciar a cadeia de qualificação no nível mais externo da biblioteca de classes .NET Framework. Isso permite que você especifique o namespace <xref:System?displayProperty=nameWithType> ou qualquer outro namespace na biblioteca de classes. O exemplo a seguir mostra isso.  
  
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
  
 Você pode usar `Global` para acessar outros namespaces de nível raiz, como <xref:Microsoft.VisualBasic?displayProperty=nameWithType>e qualquer namespace associado ao seu projeto.  
  
## <a name="global-keyword-in-namespace-statements"></a>Palavra-chave global em instruções de namespace  
 Você também pode usar a palavra-chave `Global` em uma [instrução de namespace](../../../visual-basic/language-reference/statements/namespace-statement.md). Isso permite que você defina um namespace fora do namespace raiz do seu projeto.  
  
 Todos os namespaces em seu projeto são baseados no namespace raiz do projeto.  O Visual Studio atribui o nome do projeto como o namespace raiz padrão para todo o código em seu projeto. Por exemplo, se seu projeto for nomeado `ConsoleApplication1`, seus elementos de programação pertencerão ao namespace `ConsoleApplication1`. Se você declarar `Namespace Magnetosphere`, as referências a `Magnetosphere` no projeto acessarão `ConsoleApplication1.Magnetosphere`.  
  
 Os exemplos a seguir usam a palavra-chave `Global` para declarar um namespace fora do namespace raiz do projeto.  
  
 [!code-vb[VbVbalrApplication#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#22)]  
  
 Em uma declaração de namespace, `Global` não pode ser aninhada em outro namespace.  
  
 Você pode usar a [página do aplicativo, designer de projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) para exibir e modificar o **namespace raiz** do projeto.  Para novos projetos, o **namespace raiz** usa como padrão o nome do projeto. Para fazer com que `Global` seja o namespace de nível superior, você pode limpar a entrada do **namespace raiz** para que a caixa esteja vazia. Limpar o **namespace raiz** elimina a necessidade da palavra-chave `Global` em declarações de namespace.  
  
 Se uma instrução `Namespace` declarar um nome que também seja um namespace na .NET Framework, o namespace .NET Framework ficará indisponível se a palavra-chave `Global` não for usada em um nome totalmente qualificado. Para habilitar o acesso a esse .NET Framework namespace sem usar a palavra-chave `Global`, você pode incluir a palavra-chave `Global` na instrução `Namespace`.  
  
 O exemplo a seguir tem a palavra-chave `Global` na declaração de namespace `System.Text`.  
  
 Se a palavra-chave `Global` não estiver presente na declaração de namespace, <xref:System.Text.StringBuilder> não poderá ser acessada sem especificar `Global.System.Text.StringBuilder`. Para um projeto chamado `ConsoleApplication1`, as referências a `System.Text` acessarão `ConsoleApplication1.System.Text` se a palavra-chave `Global` não foi usada.  
  
 [!code-vb[VbVbalrApplication#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrApplication/VB/module1.vb#21)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms?displayProperty=nameWithType>
- [Assemblies no .NET](../../../standard/assembly/index.md)
- [Referências e a Instrução Imports](references-and-the-imports-statement.md)
- [Instrução Imports (Tipo e Namespace .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Escrevendo código em soluções do Office](/visualstudio/vsto/writing-code-in-office-solutions)
