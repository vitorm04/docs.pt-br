---
title: "Instru&#231;&#245;es passo a passo: implementando IEnumerable(Of T) no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "fluxo de controle"
  - "fluxo de controle [Visual Basic]"
  - "interfaces enumeráveis"
  - "Estruturas de loop, otimizando o desempenho"
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#245;es passo a passo: implementando IEnumerable(Of T) no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:System.Collections.Generic.IEnumerable%601> interface é implementada por classes que podem retornar uma seqüência de um item de valores ao mesmo tempo.  A vantagem de retornar o item de dados, um por vez é que você não precisará carregar o conjunto completo de dados na memória para trabalhar com ela.  Você só precisará usar memória suficiente para carregar um único item de dados.  Classes que implementam o `IEnumerable(T)` interface pode ser usada com `For Each` loops ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um arquivo de texto grande e o retorno de cada linha do arquivo que correspondam aos critérios de pesquisa específico.  O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondam aos critérios especificados.  Para consultar o conteúdo do arquivo, usando uma consulta LINQ, o aplicativo foi possível carregar o conteúdo do arquivo em uma matriz ou uma coleção.  No entanto, carregando o arquivo inteiro em uma matriz ou coleção consumiria muito mais memória do que o necessário.  A consulta do LINQ em vez disso, foi possível consultar o conteúdo do arquivo usando uma classe enumerable, retornando somente os valores que correspondem aos critérios de pesquisa.  Consultas que retornam apenas alguns valores correspondentes consumiria muito menos memória.  
  
 Você pode criar uma classe que implementa o <xref:System.Collections.Generic.IEnumerable%601> interface para expor os dados de origem como dados enumerable.  Sua classe que implementa o `IEnumerable(T)` interface exigirá a outra classe que implementa o <xref:System.Collections.Generic.IEnumerator%601> interface para iterar por meio de dados de origem.  Essas duas classes permitem que você retornar os itens de dados seqüencialmente, como um tipo específico.  
  
 Esta explicação passo a passo, você irá criar uma classe que implementa o `IEnumerable(Of String)` interface e uma classe que implementa o `IEnumerator(Of String)` interface para ler uma texto arquivo uma linha por vez.  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## Criando a classe Enumerable  
  
||  
|-|  
|Para criar o projeto da classe enumerable|  
|1.  Em [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], no menu **File**, aponte para **New** e então clique em **Project**.<br />2.  No  **Novo projeto** na caixa a  **Tipos de projeto** painel, certifique\-se de que  **Windows** está selecionada.  Selecione  **Biblioteca de classe** na  **modelos de** painel.  No  **nome** , digite  `StreamReaderEnumerable`e, em seguida, clique em  **OK**.  O novo projeto é exibido.<br />3.  Em  **Solution Explorer**, o botão direito do mouse no arquivo Class1. vb e clique em  **Renomear**.  Renomeie o arquivo para  `StreamReaderEnumerable.vb` e pressione ENTER.  Renomear o arquivo também renomear a classe `StreamReaderEnumerable`.  Essa classe irá implementar a `IEnumerable(Of String)` interface.<br />4.  Clique com o botão direito no projeto StreamReaderEnumerable, aponte para  **Add**e, em seguida, clique em  **Novo Item**.  Selecione o modelo **Classe**.  No  **nome** , digite  `StreamReaderEnumerator.vb` e clique em  **OK**.|  
  
 A primeira classe neste projeto é a classe enumerable e implementará o `IEnumerable(Of String)` interface.  Essa interface genérica implementa o <xref:System.Collections.IEnumerable> interface e garante que os consumidores dessa classe podem acessar os valores digitados como `String`.  
  
||  
|-|  
|Para adicionar o código para implementar IEnumerable|  
|1.  Abra o arquivo StreamReaderEnumerable.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerable`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#1](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_1.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]preenche automaticamente a classe com os membros que são necessários para o `IEnumerable(Of String)` interface.<br />3.  Essa classe enumerable lê linhas de uma linha de um arquivo texto ao mesmo tempo.  Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada.<br />     [!code-vb[VbVbalrIteratorWalkthrough#2](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_2.vb)]<br />4.  A implementação da <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> método da `IEnumerable(Of String)` interface irá retornar uma nova instância da `StreamReaderEnumerator` classe.  A implementação da `GetEnumerator` método da `IEnumerable` interface pode ser feita `Private`, porque você tem que expor somente os membros da `IEnumerable(Of String)` interface.  Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `GetEnumerator` métodos com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#3](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_3.vb)]|  
  
||  
|-|  
|Para adicionar o código para implementar IEnumerator|  
|1.  Abra o arquivo StreamReaderEnumerator.vb.<br />2.  Na linha após `Public Class StreamReaderEnumerator`, digite o seguinte e pressione ENTER.<br />     [!code-vb[VbVbalrIteratorWalkthrough#4](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_4.vb)]<br />     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]preenche automaticamente a classe com os membros que são necessários para o `IEnumerator(Of String)` interface.<br />3.  A classe do enumerador abre o arquivo de texto e executa o arquivo de i\/O para ler as linhas do arquivo.  Adicione o seguinte código à classe para expor um construtor público que toma um caminho de arquivo como um parâmetro de entrada e abra o arquivo de texto para leitura.<br />     [!code-vb[VbVbalrIteratorWalkthrough#5](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_5.vb)]<br />4.  O `Current` propriedades para ambos os `IEnumerator(Of String)` e `IEnumerator` interfaces retornam o item atual do arquivo de texto como um `String`.  A implementação da `Current` propriedade da `IEnumerator` interface pode ser feita `Private`, porque você tem que expor somente os membros da `IEnumerator(Of String)` interface.  Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `Current` propriedades com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#6](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_6.vb)]<br />5.  O `MoveNext` método da `IEnumerator` interface navega para o próximo item no arquivo de texto e atualiza o valor retornado pelo `Current` propriedade.  Se houver mais itens para ler, o `MoveNext` método retorna `False`; Caso contrário, o `MoveNext` método retorna `True`.  Adicione o seguinte código ao método  `MoveNext`.<br />     [!code-vb[VbVbalrIteratorWalkthrough#7](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_7.vb)]<br />6.  O `Reset` método da `IEnumerator` interface direciona o iterador para apontar para o início do arquivo de texto e limpa o valor do item atual.  Adicione o seguinte código ao método  `Reset`.<br />     [!code-vb[VbVbalrIteratorWalkthrough#8](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_8.vb)]<br />7.  O `Dispose` método da `IEnumerator` interface garante que todos os recursos não gerenciados são liberados antes que o iterador é destruído.  O identificador de arquivo usado pelo `StreamReader` objeto é um recurso não gerenciado e deve ser fechado antes que a instância do iterador é destruída.  Substitua o código que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerado para o `Dispose` método com o código a seguir.<br />     [!code-vb[VbVbalrIteratorWalkthrough#9](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_9.vb)]|  
  
## Usando o iterador de exemplo  
 Você pode usar uma classe enumerable em seu código juntamente com as estruturas de controle que exigem um objeto que implementa `IEnumerable`, como um `For Next` loop ou uma consulta LINQ.  A exemplo a seguir mostra a `StreamReaderEnumerable` em uma consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](../../../../visual-basic/programming-guide/language-features/control-flow/codesnippet/VisualBasic/walkthrough-implementing-ienumerable-of-t_10.vb)]  
  
## Consulte também  
 [Introdução a LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Fluxo de controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Estruturas de loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)