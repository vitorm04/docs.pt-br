---
title: "Instru&#231;&#227;o For...Next (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Step"
  - "vb.Next"
  - "vb.To"
  - "vb.for"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "loops infinitos"
  - "Palavra-chave Next para... Instruções Avançar"
  - "Palavra-chave [Visual Basic] para... Instruções Avançar"
  - "Etapa palavra-chave, para... Instruções Avançar"
  - "sobrecarga de operador, para... Próxima instrução"
  - "A palavra-chave, para... Instruções Avançar"
  - "loops intermináveis"
  - "loops intermináveis"
  - "instruções de repetição"
  - "Próxima instrução, para... Avançar"
  - "instruções For...Next"
  - "estruturas de loop para... Avançar"
  - "loops infinitos"
  - "Declaração de saída para... Instruções Avançar"
  - "instrução For"
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
caps.handback.revision: 64
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o For...Next (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Repete um grupo de instruções um número de vezes especificado.  
  
## Sintaxe  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## Partes  
  
|Parte|Descrição|  
|-----------|---------------|  
|`counter`|Necessário na declaração de `For` .  Variável numérica.  A variável de controle do loop.  Para obter mais informações, consulte [Contra-argumento](#BKMK_Counter) neste tópico posteriormente.|  
|`datatype`|Opcional.  Tipo de dados de `counter`.  Para obter mais informações, consulte [Contra-argumento](#BKMK_Counter) neste tópico posteriormente.|  
|`start`|Obrigatório.  Expressão numérica.  O valor inicial de `counter`.|  
|`end`|Obrigatório.  Expressão numérica.  O valor final de `counter`.|  
|`step`|Opcional.  Expressão numérica.  A quantidade por que `counter` é incrementado sempre através do loop.|  
|`statements`|Opcional.  Uma ou mais instruções entre e `For``Next` execução que o número de vezes especificado.|  
|`Continue For`|Opcional.  Transfere controle para a próxima iteração do loop.|  
|`Exit For`|Opcional.  Transfere controle fora do loop `For`.|  
|`Next`|Obrigatório.  Termina a definição do loop `For`.|  
  
> [!NOTE]
>  A palavra\-chave de `To` é usado nessa declaração para especificar o intervalo para o contador.  Você também pode usar esta palavra\-chave em [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md) declarações e de matriz.  Para obter mais informações sobre as declarações de matriz, consulte [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## Exemplos simples  
 Você usa uma estrutura de `For`…`Next` quando você desejar repetir um conjunto de instruções um número definido de vezes.  
  
 No exemplo, inicia o variável de `index` com um valor de 1 e são incrementadas a cada iteração do loop, finalizando depois que o valor de alcances 5. de `index` .  
  
 [!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_1.vb)]  
  
 No exemplo, inicia o variável de `number` em 2 e são reduzidos por 0,25 em cada iteração do loop, finalizando depois que o valor de alcances 0 de `number` .  O argumento de `Step` de `-.25` reduz o valor por 0,25 em cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_2.vb)]  
  
> [!TIP]
>  Uma [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) funciona bem quando você não sabe com antecedência quantas vezes deve executar as instruções no loop.  No entanto, quando você pretende executar o loop um determinado número de vezes, um loop de `For`…`Next` é uma opção melhor.  Você determinar o número de iterações quando você inserir o primeiro loop.  
  
## Loops aninhados  
 Você pode aninhar loop de `For` colocando um loop dentro de outro.  O exemplo a seguir demonstra as estruturas aninhadas de `For`…`Next` que têm diferentes valores de etapa.  O loop mais externo cria uma cadeia de caracteres para cada iteração do loop.  O loop mais interno diminui uma variável do contador de loop para cada iteração do loop.  
  
 [!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_3.vb)]  
  
 Quando os loops aninhados, cada loop devem ter uma variável exclusivo de `counter` .  
  
 Você também pode aninhar estruturas de controle dentro dos diferentes tipos de se.  Para obter mais informações, consulte [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).  
  
## Para e continue para sair  
 A declaração de `Exit For` sai di loop de `For`…`Next` e o transfere controle à declaração que segue a declaração de `Next` .  
  
 O transfere o controle da declaração de `Continue For` imediatamente para a próxima iteração do loop.  Para obter mais informações, consulte [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).  
  
 O exemplo a seguir ilustra o uso das instruções de `Continue For` e de `Exit For` .  
  
 [!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_4.vb)]  
  
 Você pode colocar qualquer número de declarações de `Exit For` em um loop de `For`…`Next` .  Quando usado dentro de loops aninhados de `For`…`Next` , `Exit For` sai do controle interno do loop e da transferências de alto nível de aninhamento.  
  
 `Exit For` geralmente é usado depois que você avaliar alguma condição \(por exemplo, em um estrutura de `If`……`Then``Else` \).  Você pode usar `Exit For` nas seguintes circunstâncias:  
  
-   Continuar iterando é desnecessária ou impossível.  Um valor errôneo ou uma solicitação de finalização podem criar esta condição.  
  
-   Uma declaração de `Try``Catch`……`Finally` capturar uma exceção.  Você pode usar `Exit For` no final do bloco de `Finally` .  
  
-   Você tiver um loop interminável, que é um loop que é um grande ou mesmo número infinito de vezes.  Se você detectar tal condição, você pode usar `Exit For` para escapar do loop.  Para obter mais informações, consulte [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).  
  
## Implementação técnica  
 Quando inicia de um loop de `For`…`Next` , Visual Basic avaliarem `start`, `end`, e `step`.  Visual Basic avalia esses valores somente no momento e então designa `start` a `counter`.  Antes que o bloco de declaração é executado, o Visual Basic `counter` compara a `end`.  Se `counter` já é maior que o valor de `end` \(ou menor `step` se for negativo\), os fins de loop de `For` e ao controle passa para a declaração que segue a declaração de `Next` .  Caso contrário, o executa o bloco de declaração.  
  
 Cada vez que o Visual Basic localize a declaração de `Next` , sai `counter` por `step` e retorna a declaração de `For` .  Novamente `counter` compara a `end`, e novamente executa o bloco ou sai do loop, dependendo do resultado.  Esse processo continua até que `counter` passe `end` ou uma declaração de `Exit For` é encontrada.  
  
 O loop não para até que `counter` passe `end`.  Se `counter` é igual a `end`, o loop continua.  A comparação que determina se deve executar o bloco é `counter` \<\= `end` se `step` for positivo e `counter` \>\= `end` se `step` for negativo.  
  
 Se você alterar o valor de `counter` quando em um loop, seu código pode ser mais difícil de ler e depurar.  Alterando o valor de `start`, `end`, ou `step` não afetam os valores de iteração que foram determinados quando o loop foi inserida primeiro.  
  
 Se você aninha loop, o compilador sinaliza um erro se encontra a declaração de `Next` de um nível de aninhamento externa antes da instrução de `Next` de um nível interno.  No entanto, o compilador pode detectar este erro sobrepostos somente se você especificar `counter` em cada declaração de `Next` .  
  
### Argumento da etapa  
 O valor de `step` pode ser positivo ou negativo.  Este parâmetro determina o processamento de loop de acordo com a tabela a seguir:  
  
|**Valor da etapa**|**Se o loop é executado**|  
|------------------------|-------------------------------|  
|Positivo ou zero|\<\= `end`de`counter`|  
|Negativo|\>\= `end`de`counter`|  
  
 O valor padrão para `step` é 1.  
  
###  <a name="BKMK_Counter"></a> Contra\-argumento  
 A tabela a seguir indica se `counter` define uma nova variável local que é delimitado para o loop inteiro de `For…Next` .  Essa decisão depende se `datatype` estiver presente e se `counter` já está definido.  
  
|É `datatype` atual?|`counter` já está definido?|Resultados \(se `counter` define uma nova variável local que é delimitado para o loop inteiro de `For...Next` \)|  
|-------------------------|---------------------------------|----------------------------------------------------------------------------------------------------------------------|  
|Não|Sim|Não, porque `counter` já está definido.  Se o escopo de `counter` não é local para o procedimento, um aviso em tempo de compilação ocorre.|  
|Não|Não|Sim.  O tipo de dados é inferido de `start`, de `end`, e expressões de `step` .  Para obter informações sobre a inferência de tipos, consulte [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)[Inferência de tipo local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).|  
|Sim|Sim|Sim, mas somente se a variável existente de `counter` é definido fora do procedimento.  Essa variável permanece separado.  Se o escopo da variável existente de `counter` é local para o procedimento, um erro em tempo de compilação ocorre.|  
|Sim|Não|Sim.|  
  
 O tipo de dados de `counter` determina o tipo de iteração, que deve ser um dos seguintes tipos:  
  
-   `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, ou `Double`.  
  
-   Uma enumeração que você declare usando [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
-   `Object`.  
  
-   Um tipo `T` que possui os seguintes operadores, onde `B` é um tipo que pode ser usado em uma expressão de `Boolean` .  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 Você pode opcionalmente especificar a variável de `counter` na declaração de `Next` .  Essa sintaxe melhora a legibilidade do seu programa, especialmente se você tem loops aninhados de `For` .  Você deve especificar a variável que aparece na declaração correspondente de `For` .  
  
 `start`, `end`, e expressões de `step` podem avaliar a qualquer tipo de dados que se ampliar para o tipo de `counter`.  Se você usar um tipo definido pelo usuário para `counter`, talvez você precise definir o operador de conversão de `CType` para converter tipos de `start`, de `end`, ou de `step` para o tipo de `counter`.  
  
## Exemplo  
 O exemplo a seguir remove todos os elementos de uma lista genérica.  Em vez de [Instrução For Each...Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md), o exemplo mostra uma declaração de `For`…`Next` que executa iterações em ordem decrescente.  O exemplo usa essa técnica porque o método de `removeAt` faz com que os elementos após o elemento removido tenham um valor de índice mais baixo.  
  
 [!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_5.vb)]  
  
## Exemplo  
 O exemplo efetua iterações por uma enumeração que é declarada usando [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).  
  
 [!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_6.vb)]  
  
## Exemplo  
 No exemplo, os parâmetros da declaração usam uma classe que tem sobrecargas do operador para `+`, `-`, `>=`, e operadores de `<=` .  
  
 [!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/for-next-statement_7.vb)]  
  
## Consulte também  
 <xref:System.Collections.Generic.List%601>   
 [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Instrução While...End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md)   
 [Instrução Do...Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md)   
 [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Coleções](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)