---
title: "Tempo de vida no Visual Basic | Microsoft Docs"
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
  - "elementos declarados, tempo de vida"
  - "tempo de vida"
  - "tempo de vida, elementos declarados"
  - "tempo de vida, Visual Basic"
  - "Vida útil da variável compartilhada"
  - "variáveis estáticas, tempo de vida"
  - "variáveis estáticas, Visual Basic"
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tempo de vida no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O  *tempo de vida* de um elemento declarado é o período de tempo durante o qual ele está disponível para uso.  As variáveis são os únicos elementos que têm tempo de vida.  Para essa finalidade, o compilador trata os parâmetros do procedimento e função retorna como casos especiais de variáveis.  O tempo de vida de uma variável representa o período de tempo durante o qual ele pode armazenar um valor.  Seu valor pode alterar durante a vida útil, mas ele sempre mantém algum valor.  
  
## Diferentes tempos de vida  
 A  *variável de membro* \(declaradas no nível de módulo, fora de qualquer procedimento\) normalmente tem o mesmo tempo de vida como o elemento no qual é declarada.  Uma variável que não seja compartilhada declarada em uma classe ou estrutura existe como uma cópia separada para cada instância da classe ou estrutura na qual é declarada.  Cada tal variável tem o mesmo tempo de vida como sua instância.  No entanto, um `Shared` variável tem apenas uma vida única, que dura durante todo o tempo de execução do seu aplicativo.  
  
 A  *variável local* \(declaradas dentro de um procedimento\) existe somente enquanto está executando o procedimento no qual é declarada.  Isso se aplica também aos parâmetros do procedimento e para qualquer função de retorno.  No entanto, se esse procedimento chama a outros procedimentos, as variáveis locais retêm seus valores, enquanto os procedimentos chamados estão em execução.  
  
## Início do tempo de vida  
 Tempo de vida de uma variável local começa quando o controle entra o procedimento no qual é declarada.  Cada variável local é inicializada com o valor padrão para seu tipo de dados assim que o procedimento começa em execução.  Quando o procedimento encontra um `Dim` a instrução que especifica os valores iniciais, ele define essas variáveis a esses valores, mesmo que seu código já tinha atribuído a outros valores a eles.  
  
 Cada membro de uma variável de estrutura é inicializado como se fosse uma variável separada.  Da mesma forma, cada elemento de uma variável de matriz é inicializado individualmente.  
  
 As variáveis declaradas dentro de um bloco dentro de um procedimento \(como um `For` loop\) são inicializados na entrada para o procedimento.  Essas inicializações efeito se o seu código nunca executa o bloco ou não.  
  
## Final da vida útil  
 Quando um procedimento é encerrado, os valores das variáveis locais não são preservados, e [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] recupera sua memória.  Na próxima vez que você chama o procedimento, todas as variáveis locais são criadas afresh e reinicializadas.  
  
 Quando uma instância de uma classe ou estrutura é encerrado, suas variáveis que não seja compartilhadas perdem sua memória e seus valores.  Cada nova instância da classe ou estrutura cria e reinicializa suas variáveis que não seja compartilhadas.  No entanto, `Shared` variáveis são preservadas até que seu aplicativo será interrompida.  
  
## Extensão da vida útil  
 Se você declarar uma variável local com o `Static` a sua vida útil da palavra\-chave, é maior do que o tempo de execução de seu procedimento.  A tabela a seguir mostra como a declaração de procedimento determina quanto tempo um `Static` variável existe.  
  
|Compartilhamento e o local do procedimento|Tempo de vida da variável estático começa|Tempo de vida de variável estática extremidades|  
|------------------------------------------------|-----------------------------------------------|-----------------------------------------------------|  
|Em um módulo \(compartilhado por padrão\)|A primeira vez que o procedimento é chamado|Quando seu aplicativo parar a execução|  
|Em uma classe, `Shared` \(procedimento não é um membro de instância\)|Na primeira vez que o procedimento é chamado em uma instância específica ou no nome da classe ou estrutura própria|Quando seu aplicativo parar a execução|  
|Em uma instância de uma classe, não `Shared` \(o procedimento é um membro de instância\)|Na primeira vez que o procedimento é chamado na instância específica|Quando a instância é lançada para a coleção de lixo \(GC\)|  
  
## Variáveis estáticas de mesmo nome  
 Você pode declarar variáveis estáticas com o mesmo nome em mais de um procedimento.  Se você fizer isso, o compilador [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] considera cada variável como um elemento separado.  A inicialização de um dessas variáveis não afeta os valores das outras.  O mesmo se aplica se você definir um procedimento com um conjunto de sobrecargas e declarar uma variável estática com o mesmo nome em cada sobrecarga.  
  
## Elementos Continentes para Variáveis Estáticas  
 Você pode declarar uma variável local estática em uma classe, isto é, em um procedimento dessa classe.  No entanto, você não pode declarar uma variável local estática em uma estrutura, nem como um membro de estrutura nem como um variável local de um procedimento dentro dessa estrutura.  
  
## Exemplo  
  
### Descrição  
 O exemplo a seguir declara uma variável com a palavra\-chave [Estático](../../../../visual-basic/language-reference/modifiers/static.md).  \(Observe que você não precisa da palavra\-chave `Dim` quando o [Instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) usa um modificador, como `Static`.\)  
  
### Código  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### Comentários  
 No exemplo anterior, a variável `applesSold` continua a existir depois que o procedimento `runningTotal` retorna para o código de chamada.  Na próxima vez em que `runningTotal` é chamado, `applesSold` manterá seu valor calculado anteriormente.  
  
 Se `applesSold` tivesse sido declarada sem usar `Static`, os valores acumulados anteriormente não poderiam ser preservados entre chamadas para `runningTotal`.  Na próxima vez em que `runningTotal` fosse chamado `applesSold` teria sido recriada e inicializada com 0, e `runningTotal` teria simplesmente retornado o mesmo valor com o qual ele foi chamado.  
  
### Compilando o código  
 Você pode inicializar o valor de uma variável local estática como parte da sua declaração.  Se você declarar uma matriz para ser `Static`, você pode inicializar sua ordem \(número de dimensões\), o tamanho de cada dimensão e os valores dos elementos individuais.  
  
### Segurança  
 No exemplo anterior, você pode produzir o mesmo tempo de vida, declarando `applesSold` em nível de módulo.  Se você tivesse alterado o escopo de uma variável dessa maneira, no entanto, o procedimento não teria mais acesso exclusivo a ele.  Como outros procedimentos poderiam acessar `applesSold` e alterar seu valor, o total em execução poderia ser não confiável e o código poderia ser mais difícil manter.  
  
## Consulte também  
 [Compartilhado](../../../../visual-basic/language-reference/modifiers/shared.md)   
 [nada](../../../../visual-basic/language-reference/nothing.md)   
 [Nomes de elemento declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Escopo no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [Níveis de acesso no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Variáveis](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Solucionando problemas de tipos de dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Estático](../../../../visual-basic/language-reference/modifiers/static.md)