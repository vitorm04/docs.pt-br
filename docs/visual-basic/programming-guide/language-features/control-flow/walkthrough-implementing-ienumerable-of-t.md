---
title: Implementando IEnumerable no Visual Basic
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: be2eefdc52d38df3071d457b7a71dbac6eaa2657
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739653"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Instruções passo a passo: implementando IEnumerable(Of T) no Visual Basic
O <xref:System.Collections.Generic.IEnumerable%601> interface é implementada por classes que podem retornar uma sequência de um item de valores de cada vez. A vantagem de retornar dados de um item por vez é que você não precisa carregar o conjunto completo de dados na memória para trabalhar com ela. Você só precisará usar memória suficiente para carregar um único item de dados. As classes que implementam o `IEnumerable(T)` interface pode ser usada com `For Each` loops ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um arquivo de texto grande e retornar todas as linhas do arquivo que corresponde aos critérios de pesquisa específica. O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondem aos critérios especificados. Para consultar o conteúdo do arquivo, usando uma consulta LINQ, o aplicativo foi possível carregar o conteúdo do arquivo em uma matriz ou uma coleção. No entanto, carregar o arquivo inteiro em uma matriz ou coleção consumiria muito mais memória do que é necessário. A consulta LINQ em vez disso, pode consultar o conteúdo do arquivo por meio de uma classe enumerable, retornando somente os valores que correspondem aos critérios de pesquisa. Consultas que retornam apenas alguns valores correspondentes consumiria muito menos memória.  
  
 Você pode criar uma classe que implementa o <xref:System.Collections.Generic.IEnumerable%601> interface para expor dados de origem como dados enumeráveis. Sua classe que implementa o `IEnumerable(T)` interface exigirá outra classe que implementa o <xref:System.Collections.Generic.IEnumerator%601> interface para iterar os dados de origem. Essas duas classes permitem retornar itens de dados em sequência como um tipo específico.  
  
 Neste passo a passo, você criará uma classe que implementa o `IEnumerable(Of String)` interface e uma classe que implementa o `IEnumerator(Of String)` interface para ler um arquivo de texto uma linha por vez.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Criando a classe Enumerable  
  
**Criar o projeto de classe enumerable**

1.  No Visual Basic, sobre o **arquivo** , aponte para **New** e, em seguida, clique em **projeto**.

1.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `StreamReaderEnumerable` e clique em **OK**. O novo projeto é exibido.

1.  Na **Gerenciador de soluções**, o arquivo Class1.vb com o botão direito e clique em **Renomear**. Renomeie o arquivo como `StreamReaderEnumerable.vb` e pressione ENTER. Renomear o arquivo também renomeará a classe para `StreamReaderEnumerable`. Essa classe implementará a interface `IEnumerable(Of String)`.

1.  Clique com botão direito no projeto StreamReaderEnumerable, aponte para **Add**e, em seguida, clique em **Novo Item**. Selecione o **classe** modelo. No **nome** , digite `StreamReaderEnumerator.vb` e clique em **Okey**.

 A primeira classe no projeto é a classe enumerable e implementará o `IEnumerable(Of String)` interface. Essa interface genérica implementa o <xref:System.Collections.IEnumerable> interface e garantias de que os consumidores dessa classe podem acessar valores digitados como `String`.  
  
**Adicione o código para implementar IEnumerable**

1. Abra o arquivo StreamReaderEnumerable.vb.

2. Na linha após `Public Class StreamReaderEnumerable`, digite o seguinte e pressione ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]

   Visual Basic preenche automaticamente a classe com os membros que são exigidas pelo `IEnumerable(Of String)` interface.
  
3. Essa classe enumerable lerá linhas de um arquivo de texto uma linha por vez. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada.

   [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]

4. Sua implementação do <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método do `IEnumerable(Of String)` retorna uma nova instância da interface a `StreamReaderEnumerator` classe. A implementação do `GetEnumerator` método da `IEnumerable` interface pode ser feita `Private`, porque você tem para expor somente os membros do `IEnumerable(Of String)` interface. Substitua o código de Visual Basic gerado para o `GetEnumerator` métodos com o código a seguir.

   [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]  
  
**Adicione o código para implementar IEnumerator**

1. Abra o arquivo StreamReaderEnumerator.vb.

2. Na linha após `Public Class StreamReaderEnumerator`, digite o seguinte e pressione ENTER.

   [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]

   Visual Basic preenche automaticamente a classe com os membros que são exigidas pelo `IEnumerator(Of String)` interface.

3. A classe de enumerador abre o arquivo de texto e executa o arquivo de e/s ao ler as linhas do arquivo. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada e abra o arquivo de texto para leitura.

   [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]

4. O `Current` propriedades para ambos os `IEnumerator(Of String)` e `IEnumerator` interfaces retornam o item atual do arquivo de texto como um `String`. A implementação do `Current` propriedade do `IEnumerator` interface pode ser feita `Private`, porque você tem para expor somente os membros do `IEnumerator(Of String)` interface. Substitua o código de Visual Basic gerado para o `Current` propriedades com o código a seguir.

   [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]

5. O `MoveNext` método da `IEnumerator` interface navega para o próximo item no arquivo de texto e atualiza o valor retornado pelo `Current` propriedade. Se não houver nenhum outro item para ler, o `MoveNext` retorn `False`; caso contrário, o `MoveNext` retorno do método `True`. Adicione o seguinte código ao método de `MoveNext` .

   [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]

6. O `Reset` método da `IEnumerator` interface direciona o iterador para apontar para o início do arquivo de texto e limpa o valor do item atual. Adicione o seguinte código ao método de `Reset` .

   [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]

7. O `Dispose` método da `IEnumerator` interface garante que todos os recursos não gerenciados são liberados antes que o iterador seja destruído. O identificador de arquivo que é usado pelo `StreamReader` objeto é um recurso não gerenciado e deve ser fechado antes que a instância do iterador seja destruída. Substitua o código de Visual Basic gerado para o `Dispose` método com o código a seguir.

   [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)] 
  
## <a name="using-the-sample-iterator"></a>Usando o iterador de exemplo

 Você pode usar uma classe enumerável em seu código junto com estruturas de controle que exigem um objeto que implementa `IEnumerable`, como um `For Next` loop ou uma consulta LINQ. A exemplo a seguir mostra o `StreamReaderEnumerable` em uma consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
