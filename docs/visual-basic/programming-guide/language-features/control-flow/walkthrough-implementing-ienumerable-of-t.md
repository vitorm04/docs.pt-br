---
title: Implementando IEnumerable no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures, optimizing performance
- control flow
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 68c37c46cbceb1056d50972cdc58ddb7c7577447
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Instruções passo a passo: implementando IEnumerable(Of T) no Visual Basic
O <xref:System.Collections.Generic.IEnumerable%601>interface é implementada por classes que podem retornar uma sequência de um item de valores em um momento.</xref:System.Collections.Generic.IEnumerable%601> A vantagem de retornar dados de um item por vez é que você não precisa carregar o conjunto completo de dados na memória para trabalhar com ela. Você só precisa usar memória suficiente para carregar um único item de dados. As classes que implementam o `IEnumerable(T)` interface pode ser usada com `For Each` loops ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um arquivo de texto grande e retornar todas as linhas do arquivo que corresponde aos critérios de pesquisa específica. O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondem aos critérios especificados. Para consultar o conteúdo do arquivo, usando uma consulta LINQ, o aplicativo pode carregar o conteúdo do arquivo em uma matriz ou coleção. No entanto, carregar o arquivo inteiro em uma matriz ou coleção consumiria muito mais memória do que é necessário. A consulta LINQ em vez disso, pode consultar o conteúdo do arquivo usando uma classe enumerable, retornando somente os valores que correspondem aos critérios de pesquisa. Consultas que retornam apenas alguns valores correspondentes consumiria muito menos memória.  
  
 Você pode criar uma classe que implementa o <xref:System.Collections.Generic.IEnumerable%601>interface para expor dados de origem como dados enumerable.</xref:System.Collections.Generic.IEnumerable%601> A classe que implementa o `IEnumerable(T)` interface exigirá outra classe que implementa o <xref:System.Collections.Generic.IEnumerator%601>interface para percorrer os dados de origem.</xref:System.Collections.Generic.IEnumerator%601> Essas duas classes permitem retornar itens de dados em sequência como um tipo específico.  
  
 Neste passo a passo, você criará uma classe que implementa o `IEnumerable(Of String)` interface e uma classe que implementa o `IEnumerator(Of String)` interface para ler texto arquivo uma linha por vez.  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Criando a classe Enumerable  
  
|Para criar o projeto de classe enumerable|  
|---|  
|1.  No [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]diante de **arquivo** , aponte para **novo** e, em seguida, clique em **projeto**.<br />2.  No **novo projeto** na caixa de **tipos de projeto** painel, verifique se **Windows** está selecionado. Selecione **biblioteca de classes** no **modelos** painel. No **nome** , digite `StreamReaderEnumerable`e, em seguida, clique em **Okey**. O novo projeto é exibido.<br />3.  Em **Solution Explorer**, clique no arquivo Class1. vb e clique em **Renomear**. Renomeie o arquivo como `StreamReaderEnumerable.vb` e pressione ENTER. Renomear o arquivo também renomear a classe `StreamReaderEnumerable`. Essa classe implementará o `IEnumerable(Of String)` interface.<br />4.  Clique com botão direito no projeto StreamReaderEnumerable, aponte para **adicionar**e, em seguida, clique em **Novo Item**. Selecione o **classe** modelo. No **nome** , digite `StreamReaderEnumerator.vb` e clique em **Okey**.|  
  
 A primeira classe no projeto é a classe enumerable e implementará o `IEnumerable(Of String)` interface. Implementa essa interface genérica a <xref:System.Collections.IEnumerable>interface e garante que os consumidores dessa classe podem acessar os valores digitados como `String`.</xref:System.Collections.IEnumerable>  
  
|Para adicionar o código para implementar IEnumerable|  
|---|  
|1.  Abra o arquivo StreamReaderEnumerable.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerable`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&1;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]preenche automaticamente a classe com os membros que são exigidos pelo `IEnumerable(Of String)` interface.<br />3.  Essa classe enumerable lê linhas no texto arquivo uma linha por vez. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&2;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  Sua implementação do <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>método o `IEnumerable(Of String)` interface retornará uma nova instância do `StreamReaderEnumerator` classe</xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> A implementação do `GetEnumerator` método o `IEnumerable` interface pode ser feita `Private`, porque você precisa expor somente os membros do `IEnumerable(Of String)` interface. Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `GetEnumerator` métodos com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&3;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
|Para adicionar o código para implementar IEnumerator|  
|---|  
|1.  Abra o arquivo StreamReaderEnumerator.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerator`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&4;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]preenche automaticamente a classe com os membros que são exigidos pelo `IEnumerator(Of String)` interface.<br />3.  A classe de enumerador abre o arquivo de texto e executa o arquivo de e/s ao ler as linhas do arquivo. Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada e abra o arquivo de texto para leitura.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&5;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  O `Current` propriedades para ambos os `IEnumerator(Of String)` e `IEnumerator` interfaces retornam o item atual do arquivo de texto como um `String`. A implementação do `Current` propriedade o `IEnumerator` interface pode ser feita `Private`, porque você precisa expor somente os membros do `IEnumerator(Of String)` interface. Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `Current` propriedades com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&6;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  O `MoveNext` método o `IEnumerator` interface navega para o próximo item no arquivo de texto e atualiza o valor retornado pelo `Current` propriedade. Se não houver nenhum outro item de ler, o `MoveNext` método retorna `False`; caso contrário, o `MoveNext` método retorna `True`. Adicione o seguinte código ao método de `MoveNext` .<br />     [!code-vb[VbVbalrIteratorWalkthrough&#7;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  O `Reset` método o `IEnumerator` interface direciona o iterador para apontar para o início do arquivo de texto e limpa o valor do item atual. Adicione o seguinte código ao método de `Reset` .<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&8;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  O `Dispose` método o `IEnumerator` interface garante que todos os recursos não gerenciados são liberados antes que o iterador é destruído. O identificador de arquivo que é usado pelo `StreamReader` objeto é um recurso não gerenciado e deve ser fechado antes que a instância do iterador seja destruída. Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `Dispose` método com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough n º&9;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## <a name="using-the-sample-iterator"></a>Usando o iterador de exemplo  
 Você pode usar uma classe enumerable em seu código junto com estruturas de controle que exigem um objeto que implementa `IEnumerable`, como um `For Next` loop ou uma consulta LINQ. A exemplo a seguir mostra o `StreamReaderEnumerable` em uma consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough n º&10;](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)

