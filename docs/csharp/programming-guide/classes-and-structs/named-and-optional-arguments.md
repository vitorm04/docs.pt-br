---
title: "Argumentos nomeados e opcionais (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "namedParameter_CSharpKeyword"
  - "cs_namedParameter"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "argumentos [C#], nomeados"
  - "argumentos [C#], optional"
  - "argumentos nomeados e opcionais [C#]"
  - "argumentos nomeados [C#]"
  - "argumentos opcionais [C#]"
  - "parâmetros [C#], nomeados"
  - "parâmetros [C#], optional"
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
caps.handback.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Argumentos nomeados e opcionais (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)]apresenta os argumentos nomeados e opcionais.  *Argumentos nomeados* permitem que você especificar um argumento para um determinado parâmetro associando o argumento com o nome do parâmetro, em vez de com a posição do parâmetro na lista de parâmetros.  *Argumentos opcionais* permitem que você omita argumentos para alguns parâmetros.  Ambas as técnicas podem ser usadas com os indexadores, métodos, construtores e delegados.  
  
 Ao usar argumentos nomeados e opcionais, os argumentos são avaliados na ordem em que aparecem na lista de argumentos, não na lista de parâmetro.  
  
 Parâmetros nomeados e opcionais, quando usados em conjunto, permitem que você fornecer argumentos para apenas alguns parâmetros de uma lista de parâmetros opcionais.  Esse recurso facilita bastante a chamadas para interfaces COM, como as APIs de automação de Microsoft Office.  
  
## Argumentos nomeados  
 Argumentos nomeados liberá\-lo da necessidade de memorizar ou consultar a ordem dos parâmetros nas listas de parâmetro de métodos chamados.  O parâmetro para cada argumento pode ser especificado por nome de parâmetro.  Por exemplo, uma função que calcula o índice de massa corporal \(IMC\) pode ser chamado da forma padrão através do envio de argumentos de peso e altura por posição, na ordem definida pela função.  
  
 `CalculateBMI(123, 64);`  
  
 Se você não lembra a ordem dos parâmetros, mas você sabe que seus nomes, você pode enviar os argumentos em qualquer ordem, peso primeiro ou altura pela primeira vez.  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 Argumentos nomeados também melhoram a legibilidade do código, identificando o que representa cada argumento.  
  
 Um argumento nomeado pode seguir argumentos posicionais, conforme mostrado aqui.  
  
 `CalculateBMI(123, height: 64);`  
  
 No entanto, um argumento posicional não pode seguir um argumento nomeado.  A instrução a seguir faz com que um erro do compilador.  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## Exemplo  
 O código a seguir implementa os exemplos desta seção.  
  
 [!CODE [csProgGuideNamedAndOptional#1](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#1)]  
  
## Argumentos opcionais  
 A definição de um método, construtor, indexador ou representante pode especificar que os seus parâmetros são necessários ou que são opcionais.  Qualquer chamada deve fornecer argumentos para todos os parâmetros necessários, mas pode omitir argumentos para os parâmetros opcionais.  
  
 Cada parâmetro opcional tem um valor padrão como parte de sua definição.  Se nenhum argumento for enviado para esse parâmetro, o valor padrão é usado.  Um valor padrão deve ser um dos seguintes tipos de expressões:  
  
-   uma expressão de constante;  
  
-   uma expressão do formulário `new ValType()`, onde `ValType` é um tipo de valor, como um  [enum](../../../csharp/language-reference/keywords/enum.md) ou um  [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   uma expressão do formulário  [default\(ValType\)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md), onde `ValType` é um tipo de valor.  
  
 Parâmetros opcionais são definidos no final da lista de parâmetros, depois de todos os parâmetros obrigatórios.  Se o chamador fornece um argumento para qualquer um de uma sucessão de parâmetros opcionais, ele deve fornecer argumentos para todos os parâmetros opcionais anteriores.  Intervalos separados por ponto\-e\-vírgula na lista de argumentos não são suportados.  Por exemplo, no código a seguir, método de instância `ExampleMethod` é definido com aquele exigido e dois parâmetros opcionais.  
  
 [!CODE [csProgGuideNamedAndOptional#15](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#15)]  
  
 A seguinte chamada para `ExampleMethod` causa um erro do compilador, como um argumento foi fornecido para o terceiro parâmetro, mas não para o segundo.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 No entanto, se você souber o nome do terceiro parâmetro, você pode usar um argumento nomeado para realizá\-la.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 IntelliSense usa colchetes para indicar parâmetros opcionais, conforme mostrado na ilustração a seguir.  
  
 ![Informações rápidas do IntelliSense para o método ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional\_Parameters")  
Parâmetros opcionais em ExampleMethod  
  
> [!NOTE]
>  Você pode também declarar parâmetros opcionais usando o.NET <xref:System.Runtime.InteropServices.OptionalAttribute> classe.  `OptionalAttribute`parâmetros não exigem um valor padrão.  
  
## Exemplo  
 No exemplo a seguir, o construtor para `ExampleClass` tem um parâmetro, que é opcional.  Método de instância `ExampleMethod` tem um parâmetro obrigatório, `required`e dois parâmetros opcionais, `optionalstr` e `optionalint`.  O código em `Main` mostra as diferentes maneiras em que o construtor e o método podem ser chamados.  
  
 [!CODE [csProgGuideNamedAndOptional#2](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#2)]  
  
## Interfaces COM  
 Argumentos nomeados e opcionais, juntamente com suporte para objetos dinâmicos e outros aperfeiçoamentos, aumentam bastante a interoperabilidade com APIs, como, por exemplo, APIs de automação do Office.  
  
 Por exemplo, o [AutoFormatação](http://go.microsoft.com/fwlink/?LinkId=148201) método no Excel Microsoft Office [intervalo](http://go.microsoft.com/fwlink/?LinkId=148196) interface tem sete parâmetros, os quais são opcionais.  Esses parâmetros são mostrados na ilustração a seguir.  
  
 ![Informações rápidas do IntelliSense para o método AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat\_Parameters")  
Parâmetros de AutoFormatação  
  
 No C\# 3.0 e versões anteriores, o argumento é necessário para cada parâmetro, conforme mostrado no exemplo a seguir.  
  
 [!CODE [csProgGuideNamedAndOptional#3](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#3)]  
  
 No entanto, você pode simplificar bastante a chamada para `AutoFormat` usando os argumentos nomeados e opcionais, introduzidos no C\# 4.0.  Nomeado e argumentos opcionais permitem que você omitir o argumento para um parâmetro opcional, se você quiser alterar o valor do parâmetro padrão.  A chamada a seguir, é especificado um valor de apenas um dos sete parâmetros.  
  
 [!CODE [csProgGuideNamedAndOptional#13](../CodeSnippet/VS_Snippets_VBCSharp/csprogguidenamedandoptional#13)]  
  
 Para mais informações e um exemplo, consulte [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) e [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C\#](../Topic/How%20to:%20Access%20Office%20Interop%20Objects%20by%20Using%20Visual%20C%23%20Features%20\(C%23%20Programming%20Guide\).md).  
  
## Resolução de Sobrecarregamento  
 Uso de argumentos nomeados e opcionais afeta a resolução de sobrecarga das seguintes maneiras:  
  
-   Um método, indexador ou construtor é um candidato para execução, se cada um dos seus parâmetros é opcional ou corresponde, por nome ou por posição, para um único argumento na instrução de chamada, e esse argumento pode ser convertido para o tipo do parâmetro.  
  
-   Se for encontrado mais de um candidato, regras de resolução de sobrecarga para conversões preferenciais são aplicadas para os argumentos que são explicitamente especificados.  Argumentos omitidos para parâmetros opcionais são ignorados.  
  
-   Se dois candidatos são considerados igualmente bom, a preferência vai para um candidato que não tem parâmetros opcionais para os quais argumentos foram omitidos na chamada.  Esta é uma conseqüência de sua preferência geral na resolução de sobrecarga para candidatos que têm menos parâmetros.  
  
## Especificação da linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Consulte também  
 [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Usando o tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Usando indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)