---
title: "Resolu&#231;&#227;o de sobrecarga (Visual Basic) | Microsoft Docs"
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
  - "resolução de sobrecarga"
  - "sobrecargas, resolução"
  - "sobrecarga de procedimento, resolução de sobrecarga"
  - "procedimentos, Chamando "
  - "procedimentos, sobrecarga"
  - "assinaturas, procedimento"
  - "código do Visual Basic, procedimentos"
ms.assetid: 766115d1-4352-45fb-859f-6063e0de0ec0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resolu&#231;&#227;o de sobrecarga (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando o compilador [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] encontra uma chamada a um procedimento que está definido em várias versões sobrecarregadas, o compilador deve decidir qual dos sobrecarregamentos chamar.  Faz\-se isso realizando os seguintes passos:  
  
1.  **Acessibilidade.** Elimina qualquer sobrecarregamento com um nível de acesso que impede que o código de chamada o chame.  
  
2.  **Número de Parâmetros.** Elimina qualquer sobrecarregamento que define um número diferente de parâmetros que são fornecidos na chamada.  
  
3.  **Tipos de dados de parâmetro.** O compilador dá preferência de métodos de instância sobre métodos de extensão.  Se qualquer método de instância for encontrado que requer somente conversões para coincidir com a chamada de procedimento de expansão, todos os métodos de extensão são descartados e o compilador continua com apenas os candidatos de método de instância.  Se nenhum desses métodos de instância for encontrado, ele continua com os métodos de extensão e de instância.  
  
     Nesta etapa, ele elimina qualquer sobrecarga para os quais os tipos de dados dos argumentos de chamada não podem ser convertidos para os tipos de parâmetro definidos na sobrecarga.  
  
4.  **Conversões explicitas de restrição.** Elimina qualquer sobrecarregamento que exige uma conversão de estreitamento dos tipos de argumento de chamada ao tipos definidos de parâmetro.  Isto é verdadeiro se o interruptor de verificação de tipo \([Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)\) estiver na posição `On` ou `Off`.  
  
5.  **Alargamento Mínimo.** O compilador considera os restantes métodos sobrecarregados em pares.  Para cada par, compara o tipo de dados dos parâmetros definidos.  Se os tipos em um dos sobrecarregamentos todos alargam para os tipos correspondentes no outro, o compilador elimina o último.  Ou seja, ele retém a sobrecarga que requer o mínimo de ampliação.  
  
6.  **Candidato Único.** Continua considerando sobrecarregamentos em pares até que reste apenas um sobrecarregamento, e resolve a chamada para aquele sobregarregamento.  Se o compilador não pode reduzir os sobrecarregamentos a um candidato único, ele gera um erro.  
  
 A ilustração a seguir mostra o processo que determina qual chamar de um conjunto de versões sobrecarregadas.  
  
 ![Diagrama de fluxo do processo de resolução de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/media/overloadres.gif "OverloadRes")  
Resolução entre versões sobrecarregadas  
  
 O exemplo a seguir ilustra este processo de resolução de sobrecarregamento.  
  
 [!code-vb[VbVbcnProcedures#62](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/overload-resolution_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#63](../../../../visual-basic/programming-guide/language-features/procedures/codesnippet/VisualBasic/overload-resolution_2.vb)]  
  
 Na primeira chamada, o compilador elimina o primeiro sobrecarregamento porque o tipo do primeiro argumento \(`Short`\) estreita ao tipo do parâmetro correspondente \(`Byte`\).  Então elimina o terceiro sobrecarregamento porque cada tipo de argumento no segundo sbrecarregamento \(`Short` e `Single`\) alarga ao tipo correspondente no terceiro sobrecarregamento \(`Integer` e `Single`\).  O segundo sobrecarregamento requer menos alargamento, então o compilador usa\-o para a chamada.  
  
 Na segunda chamada, o compilador não pode eliminar qualquer dos sobrecarregamentos na base do estreitamento.  Elimina o terceiro sobrecarregamento pela mesma razão que na primeira chamada, porque pode chamar o segundo sobrecarregamento com menos alargamento de tipos de argumento.  Entretanto, o compilador não pode resolver entre o primeiro e segundo sobrecarregamentos.  Cada um possui tipo definido de parâmetro que alarga para o tipo correspondente no outro \(`Byte` a `Short`, mas `Single` a `Double`\).  O compilador, por isso, gera um erro de resolução de sobrecarregamento.  
  
## Argumentos Overloaded Optional e ParamArray  
 Se dois sobrecarregamentos de um procedimento possuem assinaturas idênticas exceto que o último parâmetro é declarado [Opcional](../../../../visual-basic/language-reference/modifiers/optional.md) em um e [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) no outro, o compilador resolve uma chamada para aquele procedimento como se segue:  
  
|||  
|-|-|  
|Se a chamada fornecer o último argumento como|O compilador resolve a chamada ao sobrecarregamento declarando o último argumento como|  
|Nenhum valor \(argumento omitido\)|`Optional`|  
|Um valor único|`Optional`|  
|Dois ou mais valores numa lista separada por vírgula|`ParamArray`|  
|Uma matriz de qualquer comprimento \(incluindo uma matriz vazia\)|`ParamArray`|  
  
## Consulte também  
 [Parâmetros opcionais](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Matrizes de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Sobrecarga de procedimento](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Solucionando problemas de procedimentos](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Como definir várias versões de um procedimento](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [Como chamar um procedimento sobrecarregado](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [Como sobrecarregar um procedimento que usa parâmetros opcionais](../Topic/How%20to:%20Overload%20a%20Procedure%20that%20Takes%20Optional%20Parameters%20\(Visual%20Basic\).md)   
 [Como sobrecarregar um procedimento que usa um número indefinido de parâmetros](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerações sobre procedimentos de sobrecarga](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Sobrecargas](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Métodos de extensão](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)