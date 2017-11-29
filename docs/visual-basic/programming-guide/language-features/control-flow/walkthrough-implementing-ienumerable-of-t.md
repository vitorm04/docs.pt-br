---
title: Implementando IEnumerable no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45b4008f0bf3ae0f303aa029e7bff5b82ab6f259
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Instruções passo a passo: implementando IEnumerable(Of T) no Visual Basic
O <xref:System.Collections.Generic.IEnumerable%601> interface é implementada por classes que podem retornar uma sequência de um item de valores de cada vez. A vantagem de retornando dados de um item por vez é que você não precisa carregar o conjunto completo de dados na memória para trabalhar com ele. Você só precisa usar memória suficiente para carregar um único item de dados. As classes que implementam o `IEnumerable(T)` interface pode ser usada com `For Each` loops ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um arquivo de texto grande e retorna cada linha do arquivo que corresponde aos critérios de pesquisa específica. O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondem aos critérios especificados. Para consultar o conteúdo do arquivo usando uma consulta LINQ, o aplicativo foi possível carregar o conteúdo do arquivo em uma matriz ou uma coleção. No entanto, carregar o arquivo inteiro em uma matriz ou coleção consumiria muito mais memória do que é necessário. A consulta LINQ em vez disso, pode consultar o conteúdo do arquivo usando uma classe enumerable, retornando somente os valores que correspondem aos critérios de pesquisa. Consultas que retornam apenas alguns valores correspondentes consumiria muito menos memória.  
  
 Você pode criar uma classe que implementa o <xref:System.Collections.Generic.IEnumerable%601> interface para expor a fonte de dados como dados enumeráveis. A classe que implementa o `IEnumerable(T)` interface exigirá outra classe que implementa o <xref:System.Collections.Generic.IEnumerator%601> interface para iterar os dados de origem. Essas duas classes permitem retornar itens de dados em sequência como um tipo específico.  
  
 Neste passo a passo, você criará uma classe que implementa o `IEnumerable(Of String)` interface e uma classe que implementa o `IEnumerator(Of String)` interface para ler uma linha de um arquivo texto por vez.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Criando a classe enumerável  
  
|Para criar o projeto de classe enumerável|  
|---|  
|1.  Em [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.<br />2.  Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `StreamReaderEnumerable` e clique em **OK**. O novo projeto é exibido.<br />3.  Em **Solution Explorer**, clique no arquivo Class1. vb e clique em **Renomear**. Renomeie o arquivo como `StreamReaderEnumerable.vb` e pressione ENTER. Renomear o arquivo também renomeará a classe para `StreamReaderEnumerable`. Essa classe implementará a interface `IEnumerable(Of String)`.<br />4.  Clique com botão direito no projeto StreamReaderEnumerable, aponte para **adicionar**e, em seguida, clique em **Novo Item**. Selecione o **classe** modelo. No **nome** , digite `StreamReaderEnumerator.vb` e clique em **Okey**.|  
  
 A primeira classe neste projeto é a classe enumerável e implementar o `IEnumerable(Of String)` interface. Essa interface genérica implementa o <xref:System.Collections.IEnumerable> interface e garante que os consumidores dessa classe podem acessar valores digitados como `String`.  
  
|Para adicionar o código para implementar IEnumerable|  
|---|  
|1.  Abra o arquivo StreamReaderEnumerable.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerable`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]preenche automaticamente a classe com os membros necessários para o `IEnumerable(Of String)` interface.<br />3.  Essa classe enumerável lê linhas em uma linha de um arquivo texto por vez. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Sua implementação do <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método o `IEnumerable(Of String)` interface retornará uma nova instância do `StreamReaderEnumerator` classe. A implementação do `GetEnumerator` método o `IEnumerable` interface pode ser feita `Private`, pois você precisa expor somente os membros do `IEnumerable(Of String)` interface. Substitua o código que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gerado para o `GetEnumerator` métodos com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Para adicionar o código para implementar IEnumerator|  
|---|  
|1.  Abra o arquivo StreamReaderEnumerator.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerator`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]preenche automaticamente a classe com os membros necessários para o `IEnumerator(Of String)` interface.<br />3.  A classe de enumerador abre o arquivo de texto e executa o arquivo de e/s ao ler as linhas do arquivo. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada e abra o arquivo de texto para leitura.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  O `Current` propriedades para ambos os `IEnumerator(Of String)` e `IEnumerator` interfaces retornam o item atual do arquivo de texto como um `String`. A implementação do `Current` propriedade do `IEnumerator` interface pode ser feita `Private`, pois você precisa expor somente os membros do `IEnumerator(Of String)` interface. Substitua o código que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gerado para o `Current` propriedades com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  O `MoveNext` método o `IEnumerator` interface navega para o próximo item no arquivo de texto e atualiza o valor retornado pelo `Current` propriedade. Se não houver nenhum outro item para ler, o `MoveNext` método retorna `False`; caso contrário, o `MoveNext` método retornará `True`. Adicione o seguinte código ao método de `MoveNext` .<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  O `Reset` método o `IEnumerator` interface direciona o iterador para apontar para o início do arquivo de texto e limpa o valor do item atual. Adicione o seguinte código ao método de `Reset` .<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  O `Dispose` método o `IEnumerator` interface garante que todos os recursos não gerenciados são liberados antes que o iterador é destruído. O identificador de arquivo que é usado pelo `StreamReader` objeto é um recurso não gerenciado e devem ser fechado antes da instância de iterador é destruída. Substitua o código que [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gerado para o `Dispose` método com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Usando o iterador de exemplo  
 Você pode usar uma classe enumerável em seu código junto com estruturas de controle que exigem um objeto que implementa `IEnumerable`, como um `For Next` loop ou uma consulta LINQ. A exemplo a seguir mostra o `StreamReaderEnumerable` em uma consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
