---
title: "Argumentos nomeados e opcionais (Guia de Programação em C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9827553c1362d92bdf68a50e840b33474a22dcaa
ms.lasthandoff: 03/13/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a>Argumentos nomeados e opcionais (Guia de Programação em C#)
[!INCLUDE[csharp_dev10_long](../../../csharp/programming-guide/classes-and-structs/includes/csharp_dev10_long_md.md)] apresenta argumentos nomeados e opcionais. *Argumentos nomeados* permitem especificar um argumento para um parâmetro específico associando o argumento ao nome do parâmetro e não com à posição do parâmetro na lista de parâmetros. *Argumentos opcionais* permitem omitir argumentos para alguns parâmetros. Ambas as técnicas podem ser usadas com os métodos, indexadores, construtores e delegados.  
  
 Quando você usa argumentos nomeados e opcionais, os argumentos são avaliados na ordem em que aparecem na lista de argumentos e não na lista de parâmetros.  
  
 Os parâmetros nomeados e opcionais, quando usados em conjunto, permitem que você forneça argumentos para apenas alguns parâmetros de uma lista de parâmetros opcionais. Essa capacidade facilita bastante a chamadas para interfaces COM como as APIs de Automação do Microsoft Office.  
  
## <a name="named-arguments"></a>Argumentos nomeados  
 Os argumentos nomeados liberam você da necessidade de lembrar ou procurar a ordem dos parâmetros nas listas de parâmetros de métodos chamados. O parâmetro para cada argumento pode ser especificado pelo nome do parâmetro. Por exemplo, uma função que calcula o IMC (índice de massa corporal) pode ser chamada da maneira padrão enviando argumentos para peso e altura pela posição, na ordem definida pela função.  
  
 `CalculateBMI(123, 64);`  
  
 Se você não lembrar a ordem dos parâmetros, mas souber os nomes, pode enviar os argumentos em qualquer ordem, peso primeiro ou altura primeiro.  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 Os argumentos nomeados também melhoram a legibilidade do código identificando o que cada argumento representa.  
  
 Um argumento nomeado pode seguir argumentos posicionais, conforme mostrado aqui.  
  
 `CalculateBMI(123, height: 64);`  
  
 No entanto, um argumento posicional não pode seguir um argumento nomeado. A instrução a seguir causa um erro do compilador.  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a>Exemplo  
 O código a seguir implementa os exemplos desta seção.  
  
 [!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]  
  
## <a name="optional-arguments"></a>Argumentos opcionais  
 A definição de um método, construtor, indexador ou delegado pode especificar que seus parâmetros são obrigatórios ou que são opcionais. Qualquer chamada deve fornecer argumentos para todos os parâmetros necessários, mas pode omitir argumentos para parâmetros opcionais.  
  
 Cada parâmetro opcional tem um valor padrão como parte de sua definição. Se nenhum argumento é enviado para esse parâmetro, o valor padrão é usado. Um valor padrão deve ser um dos seguintes tipos de expressões:  
  
-   uma expressão de constante;  
  
-   uma expressão da forma `new ValType()`, em que `ValType` é um tipo de valor, como um [enum](../../../csharp/language-reference/keywords/enum.md) ou um [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);  
  
-   uma expressão da forma [default(ValType)](../../../csharp/programming-guide/generics/default-keyword-in-generic-code.md), em que `ValType` é um tipo de valor.  
  
 Os parâmetros opcionais são definidos no final da lista de parâmetros, depois de todos os parâmetros obrigatórios. Se o chamador fornecer um argumento para qualquer um de uma sucessão de parâmetros opcionais, ele deverá fornecer argumentos para todos os parâmetros opcionais anteriores. Não há suporte para intervalos separados por vírgula na lista de argumentos. Por exemplo, no código a seguir, método de instância `ExampleMethod` está definido com um parâmetro obrigatório e dois opcionais.  
  
 [!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]  
  
 A chamada para `ExampleMethod` a seguir causa um erro do compilador, porque um argumento é fornecido para o terceiro parâmetro, mas não para o segundo.  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 No entanto, se você souber o nome do terceiro parâmetro, poderá usar um argumento nomeado para realizar a tarefa.  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 O IntelliSense usa colchetes para indicar parâmetros opcionais, conforme mostrado na ilustração a seguir.  
  
 ![Informações rápidas do IntelliSense para o método ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")  
Parâmetros opcionais no ExampleMethod  
  
> [!NOTE]
>  Você também pode declarar parâmetros opcionais usando a classe <xref:System.Runtime.InteropServices.OptionalAttribute> do .NET. Os parâmetros `OptionalAttribute` não exigem um valor padrão.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o construtor para `ExampleClass` tem um parâmetro, que é opcional. O método de instância `ExampleMethod` tem um parâmetro obrigatório, `required` e dois parâmetros opcionais, `optionalstr` e `optionalint`. O código em `Main` mostra as diferentes maneiras em que o construtor e o método podem ser invocados.  
  
 [!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]  
  
## <a name="com-interfaces"></a>Interfaces COM  
 Os argumentos nomeados e opcionais, juntamente com suporte para objetos dinâmicos e outros aprimoramentos, aprimoram enormemente a interoperabilidade com APIs COM, como APIs de Automação do Office.  
  
 Por exemplo, o método [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) na interface [Range](http://go.microsoft.com/fwlink/?LinkId=148196) do Microsoft Office Excel tem sete parâmetros, todos opcionais. Esses parâmetros são mostrados na ilustração a seguir.  
  
 ![Informações rápidas do IntelliSense para o método AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")  
Parâmetros de AutoFormat  
  
 No C# 3.0 e versões anteriores, é necessário um argumento para cada parâmetro, como mostrado no exemplo a seguir.  
  
 [!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]  
  
 No entanto, você pode simplificar muito a chamada para `AutoFormat` usando argumentos nomeados e opcionais, introduzidos no C# 4.0. Os argumentos nomeados e opcionais permitem que você omita o argumento para um parâmetro opcional se não desejar alterar o valor padrão do parâmetro. Na chamada a seguir, um valor é especificado para apenas um dos sete parâmetros.  
  
 [!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]  
  
 Para obter mais informações e exemplos, consulte [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) e [Como acessar objetos de interoperabilidade do Office usando recursos do Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
## <a name="overload-resolution"></a>Resolução de sobrecarga  
 O uso de argumentos nomeados e opcionais afeta a resolução de sobrecarga das seguintes maneiras:  
  
-   Um método, indexador ou construtor é um candidato para a execução se cada um dos parâmetros é opcional ou corresponde, por nome ou posição, a um único argumento na instrução de chamada e esse argumento pode ser convertido para o tipo do parâmetro.  
  
-   Se mais de um candidato for encontrado, as regras de resolução de sobrecarga de conversões preferenciais serão aplicadas aos argumentos que são especificados explicitamente. Os argumentos omitidos para parâmetros opcionais são ignorados.  
  
-   Se dois candidatos são considerados igualmente bons, a preferência vai para um candidato que não tem parâmetros opcionais para os quais argumentos foram omitidos na chamada. Esta é uma consequência da preferência geral na resolução de sobrecarga de candidatos que têm menos parâmetros.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Como usar argumentos nomeados e opcionais na programação do Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Usando o Tipo dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Usando construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)   
 [Usando indexadores](../../../csharp/programming-guide/indexers/using-indexers.md)
