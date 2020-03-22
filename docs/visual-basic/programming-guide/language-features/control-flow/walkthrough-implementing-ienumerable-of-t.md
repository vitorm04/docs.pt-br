---
title: Implementando IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266905"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Instruções passo a passo: implementando IEnumerable(Of T) no Visual Basic
A <xref:System.Collections.Generic.IEnumerable%601> interface é implementada por classes que podem retornar uma seqüência de valores um item de cada vez. A vantagem de devolver dados um item de cada vez é que você não precisa carregar o conjunto completo de dados na memória para trabalhar com ele. Você só precisa usar memória suficiente para carregar um único item dos dados. As classes `IEnumerable(T)` que implementam `For Each` a interface podem ser usadas com loops ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um grande arquivo de texto e retornar cada linha do arquivo que corresponda a critérios de pesquisa específicos. O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondem aos critérios especificados. Para consultar o conteúdo do arquivo usando uma consulta LINQ, o aplicativo poderia carregar o conteúdo do arquivo em uma matriz ou uma coleção. No entanto, carregar todo o arquivo em uma matriz ou coleção consumiria muito mais memória do que o necessário. A consulta LINQ poderia, em vez disso, consultar o conteúdo do arquivo usando uma classe enumerada, retornando apenas valores que correspondem aos critérios de pesquisa. Consultas que retornam apenas alguns valores correspondentes consumiriam muito menos memória.  
  
 Você pode criar uma classe <xref:System.Collections.Generic.IEnumerable%601> que implemente a interface para expor os dados de origem como dados enumerados. Sua classe que `IEnumerable(T)` implementa a interface exigirá <xref:System.Collections.Generic.IEnumerator%601> outra classe que implemente a interface para iterar através dos dados de origem. Essas duas classes permitem que você devolva itens de dados sequencialmente como um tipo específico.  
  
 Neste passo a passo, você criará `IEnumerable(Of String)` uma classe que implementa `IEnumerator(Of String)` a interface e uma classe que implementa a interface para ler um arquivo de texto uma linha de cada vez.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Criando a Classe Enumerada  
  
**Crie o projeto de classe enumerado**

1. No Visual Basic, no menu **Arquivo,** aponte para **Novo** e clique em **Projeto**.

1. Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `StreamReaderEnumerable` e clique em **OK**. O novo projeto é exibido.

1. No **Solution Explorer,** clique com o botão direito do mouse no arquivo Class1.vb e clique **em Renomear**. Renomeie o arquivo como `StreamReaderEnumerable.vb` e pressione ENTER. Renomear o arquivo também renomeará a classe para `StreamReaderEnumerable`. Essa classe implementará a interface `IEnumerable(Of String)`.

1. Clique com o botão direito do mouse no projeto StreamReaderEnumerable, aponte para **Adicionar**e clique em **Novo Item**. Selecione o modelo **Classe.** Na caixa **Nome**, digite `StreamReaderEnumerator.vb` e clique em **OK**.

 A primeira classe deste projeto é a classe `IEnumerable(Of String)` enumerada e implementará a interface. Esta interface genérica <xref:System.Collections.IEnumerable> implementa a interface e garante que os `String`consumidores desta classe possam acessar valores digitados como .  
  
**Adicione o código para implementar IEnumerable**

1. Abra o arquivo StreamReaderEnumerable.vb.

2. Na linha `Public Class StreamReaderEnumerable`após , digite o seguinte e pressione ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   O Visual Basic preenche automaticamente a classe com `IEnumerable(Of String)` os membros que são exigidos pela interface.
  
3. Esta classe enumerada lerá linhas de um arquivo de texto uma linha de cada vez. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como parâmetro de entrada.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Sua implementação <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> do `IEnumerable(Of String)` método da interface retornará `StreamReaderEnumerator` uma nova instância da classe. A implementação `GetEnumerator` do `IEnumerable` método da `Private`interface pode ser feita, porque `IEnumerable(Of String)` você tem que expor apenas os membros da interface. Substitua o código que `GetEnumerator` o Visual Basic gerou para os métodos com o seguinte código.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Adicione o código para implementar o IEnumerator**

1. Abra o arquivo StreamReaderEnumerator.vb.

2. Na linha `Public Class StreamReaderEnumerator`após , digite o seguinte e pressione ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   O Visual Basic preenche automaticamente a classe com `IEnumerator(Of String)` os membros que são exigidos pela interface.

3. A classe enumerador abre o arquivo de texto e executa a I/O do arquivo para ler as linhas do arquivo. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como parâmetro de entrada e abre o arquivo de texto para leitura.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. As `Current` propriedades para `IEnumerator(Of String)` `IEnumerator` as interfaces e interfaces retornam o `String`item atual do arquivo de texto como um . A implementação `Current` da `IEnumerator` propriedade da `Private`interface pode ser feita, porque `IEnumerator(Of String)` você tem que expor apenas os membros da interface. Substitua o código que `Current` o Visual Basic gerou para as propriedades pelo seguinte código.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. O `MoveNext` método `IEnumerator` da interface navega até o próximo item no arquivo de texto `Current` e atualiza o valor que é devolvido pela propriedade. Se não houver mais itens para `MoveNext` ler, `False`o método retorna; caso contrário, `MoveNext` `True`o método retorna . Adicione o seguinte código ao `MoveNext` método.

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. O `Reset` método `IEnumerator` da interface direciona o iterador para apontar para o início do arquivo de texto e limpa o valor atual do item. Adicione o seguinte código ao `Reset` método.

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. O `Dispose` método `IEnumerator` da interface garante que todos os recursos não gerenciados sejam liberados antes que o iterizador seja destruído. O cabo de arquivo `StreamReader` usado pelo objeto é um recurso não gerenciado e deve ser fechado antes que a instância do tempo rétero seja destruída. Substitua o código que `Dispose` o Visual Basic gerou para o método pelo seguinte código.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a>Usando o éterizador de amostras

 Você pode usar uma classe enumerada em seu código juntamente `IEnumerable`com estruturas `For Next` de controle que requerem um objeto que implementa, como um loop ou uma consulta LINQ. O exemplo a `StreamReaderEnumerable` seguir mostra a consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Confira também

- [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
