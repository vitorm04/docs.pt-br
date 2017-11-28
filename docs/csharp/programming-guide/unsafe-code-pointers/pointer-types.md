---
title: "Tipos de ponteiro (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0699793e91199cc623c0d13e42937c8b919e992a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-types-c-programming-guide"></a>Tipos de ponteiro (Guia de Programação em C#)
Em um contexto inseguro, um tipo pode ser de ponteiro, valor ou referência. Uma declaração de tipo de ponteiro usa uma das seguintes formas:  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 Alguns dos seguintes tipos podem ser um tipo de ponteiro:  
  
-   [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md) ou [bool](../../../csharp/language-reference/keywords/bool.md).  
  
-   Qualquer tipo [enum](../../../csharp/language-reference/keywords/enum.md).  
  
-   Qualquer tipo de ponteiro.  
  
-   Qualquer struct definido pelo usuário que contenha somente campos de tipos não gerenciados.  
  
 Os tipos de ponteiro não são herdados de [objeto](../../../csharp/language-reference/keywords/object.md) e não há nenhuma conversão entre tipos de ponteiro e `object`. Além disso, as conversões boxing e unboxing não oferecem suporte a ponteiros. No entanto, você pode converter entre diferentes tipos de ponteiro e tipos de ponteiro e tipos integrais.  
  
 Quando você designa vários ponteiros na mesma declaração, o asterisco (*) é escrito junto apenas com o tipo subjacente; ele não é usado como um prefixo para cada nome de ponteiro. Por exemplo:  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 Um ponteiro não pode apontar para uma referência ou um [struct](../../../csharp/language-reference/keywords/struct.md) que contenha referências, pois uma referência de objeto pode ser coletada como lixo mesmo se um ponteiro estiver apontando para ela. O coletor de lixo não acompanha se um objeto está sendo apontado por qualquer tipo de ponteiro.  
  
 O valor da variável de ponteiro do tipo `myType*` é o endereço de uma variável do tipo `myType`. Estes são exemplos de declarações de tipos de ponteiro:  
  
|Exemplo|Descrição|  
|-------------|-----------------|  
|`int* p`|`p` é um ponteiro para um inteiro.|  
|`int** p`|`p` é um ponteiro para um ponteiro para um inteiro.|  
|`int*[] p`|`p` é uma matriz unidimensional de ponteiros para inteiros.|  
|`char* p`|`p` é um ponteiro para um caractere.|  
|`void* p`|`p` é um ponteiro para um tipo desconhecido.|  
  
 O operador de indireção de ponteiro * pode ser usado para acessar o conteúdo no local apontado pela variável de ponteiro. Por exemplo, considere a seguinte declaração:  
  
```  
int* myVariable;  
```  
  
 A expressão `*myVariable` denota a variável `int` encontrada no endereço contido em `myVariable`.  
  
 Há vários exemplos de ponteiros nos tópicos [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) e [Conversões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).  O exemplo a seguir mostra a necessidade da palavra-chave `unsafe` e a instrução `fixed` e como incrementar um ponteiro interior.  Você pode colar esse código na função principal de um aplicativo de console para executá-lo. (Lembre-se de habilitar o código não seguro no **Designer de Projeto**, escolha **Projeto**, **Propriedades** na barra de menus e selecione **Permitir código não seguro** na guia **Compilar**.)  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 Você não pode aplicar o operador de indireção para um ponteiro do tipo `void*`. No entanto, você pode usar uma conversão para converter um ponteiro nulo em qualquer outro tipo de ponteiro e vice-versa.  
  
 Um ponteiro pode ser `null`. Aplicar o operador de indireção a um ponteiro nulo causa um comportamento definido por implementação.  
  
 Lembre-se de que transmitir ponteiros entre métodos pode causar comportamento indefinido. Exemplos estão retornando um ponteiro para uma variável local através de um parâmetro Out ou Ref ou como o resultado da função. Se o ponteiro foi definido em um bloco fixo, a variável à qual ele aponta não pode mais ser corrigida.  
  
 A tabela a seguir lista os operadores e as instruções que podem operar em ponteiros em um contexto inseguro:  
  
|Operador/Instrução|Use|  
|-------------------------|---------|  
|*|Executa indireção de ponteiro.|  
|->|Acessa um membro de um struct através de um ponteiro.|  
|[]|Indexa um ponteiro.|  
|`&`|Obtém o endereço de uma variável.|  
|++ e --|Incrementa e decrementa ponteiros.|  
|+ e -|Executa aritmética de ponteiros.|  
|==, !=, \<, >, \<= e >=|Compara ponteiros.|  
|`stackalloc`|Aloca memória na pilha.|  
|Instrução `fixed`|Corrige temporariamente uma variável para que seu endereço possa ser encontrado.|  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Conversões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [Expressões de ponteiro](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [Tipos](../../../csharp/language-reference/keywords/types.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)  
 [Conversão boxing e unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
