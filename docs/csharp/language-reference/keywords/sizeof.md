---
title: sizeof (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 83038255160ec778c71120566cf8f99092761add
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270572"
---
# <a name="sizeof-c-reference"></a>sizeof (Referência de C#)
Usado para obter o tamanho, em bytes, de um tipo não gerenciado. Tipos não gerenciados incluem os tipos internos listados na tabela a seguir e também o seguinte:  
  
-   Tipos enum  
  
-   Tipos de ponteiro  
  
-   Structs definidos pelo usuário que não contêm campos ou propriedades que são tipos de referência  
  
 O exemplo a seguir mostra como recuperar o tamanho de um `int`:  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a>Comentários  
 A partir da versão 2.0 do C#, aplicar `sizeof` a tipos internos não exige mais que o modo [não seguro](../../../csharp/language-reference/keywords/unsafe.md) seja usado.  
  
 O operador `sizeof` não pode ser sobrecarregado. Os valores retornados pelo operador `sizeof` são do tipo `int`. A tabela a seguir mostra os valores constantes que são substituídos por expressões `sizeof` que têm determinados tipos internos como operandos.  
  
|Expressão|Valor constante|  
|----------------|--------------------|  
|`sizeof(sbyte)`|1|  
|`sizeof(byte)`|1|  
|`sizeof(short)`|2|  
|`sizeof(ushort)`|2|  
|`sizeof(int)`|4|  
|`sizeof(uint)`|4|  
|`sizeof(long)`|8|  
|`sizeof(ulong)`|8|  
|`sizeof(char)`|2 (Unicode)|  
|`sizeof(float)`|4|  
|`sizeof(double)`|8|  
|`sizeof(decimal)`|16|  
|`sizeof(bool)`|1|  
  
 Para todos os outros tipos, incluindo structs, o operador `sizeof` pode ser usado somente em blocos de código não seguro. Embora você possa usar o método <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, o valor retornado por esse método não é sempre o mesmo que o valor retornado por `sizeof`. <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retorna o tamanho após o tipo ter passado por marshaling, enquanto `sizeof` retorna o tamanho como ele foi alocado pelo Common Language Runtime, incluindo qualquer preenchimento.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Palavras-chave do operador](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [enum](../../../csharp/language-reference/keywords/enum.md)  
 [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [Estruturas](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [Constantes](../../../csharp/programming-guide/classes-and-structs/constants.md)
