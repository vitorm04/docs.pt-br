---
title: "Tipo de dados definido pelo usuário | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
dev_langs:
- VB
helpviewer_keywords:
- user-defined data types, Visual Basic
- user-defined types
- structures, as user-defined data types
- user-defined types, Visual Basic
- user-defined types, structure declaration
- user-defined types, structures in Visual Basic
- user-defined data types, structure declaration
- data types [Visual Basic], assigning
- Structure statement
- data types [Visual Basic], user-defined
- user-defined data types, structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: e76a556e21e5a359aafd294c106f9ca1fb6151e2
ms.lasthandoff: 03/13/2017

---
# <a name="user-defined-data-type"></a>Tipo de dados definido pelo usuário
Mantém os dados em um formato que você definir. O `Structure` instrução define o formato.  
  
 Versões anteriores do Visual Basic suportam o tipo definido pelo usuário (UDT). A versão atual expande o UDT um *estrutura*. Uma estrutura é uma concatenação de um ou mais *membros* de vários tipos de dados. Visual Basic trata uma estrutura como uma única unidade, embora você também pode acessar seus membros individualmente.  
  
## <a name="remarks"></a>Comentários  
 Definir e usar um tipo de estrutura de dados quando você precisa combinar vários tipos de dados em uma única unidade, ou quando nenhum dos tipos de dados elementares atende às suas necessidades.  
  
 O valor padrão de um tipo de dados de estrutura consiste a combinação dos valores padrão de cada um dos seus membros.  
  
## <a name="declaration-format"></a>Formato de declaração  
 Uma declaração de estrutura começa com o [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) e termina com o `End``Structure` instrução. O `Structure` instrução fornece o nome da estrutura, que também é o identificador do tipo de dados é definir a estrutura. Outras partes do código podem usar esse identificador para declarar variáveis, parâmetros e função retornam valores desse da estrutura tipo de dados.  
  
 As declarações entre o `Structure` e `End``Structure` instruções definem os membros da estrutura.  
  
## <a name="member-access-levels"></a>Níveis de acesso de membro  
 Você deve declarar cada membro usando um [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou uma instrução que especifica o nível de acesso, como [pública](../../../visual-basic/language-reference/modifiers/public.md), [amigo](../../../visual-basic/language-reference/modifiers/friend.md), ou [particular](../../../visual-basic/language-reference/modifiers/private.md). Se você usar um `Dim` instrução, os padrões de nível de acesso para público.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Consumo de memória.** Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo de memória total de uma estrutura somando as alocações de armazenamento nominais de seus membros. Além disso, você não pode presumir que a ordem de armazenamento em memória é o mesmo que a ordem da declaração. Se você precisa controlar o layout de armazenamento de uma estrutura, você pode aplicar o <xref:System.Runtime.InteropServices.StructLayoutAttribute>de atributo para o `Structure` instrução.</xref:System.Runtime.InteropServices.StructLayoutAttribute>  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, como objetos Automation ou COM, tenha em mente que os tipos definidos pelo usuário em outros ambientes não são compatíveis com o Visual Basic estruturam tipos.  
  
-   **Ampliação.** Não há nenhuma conversão automática de ou para qualquer tipo de dados da estrutura. Você pode definir operadores de conversão em sua estrutura usando o [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md), e você pode declarar cada operador de conversão ser `Widening` ou `Narrowing`.  
  
-   **Caracteres de tipo.** Tipos de dados de estrutura não têm nenhum caractere de tipo literal ou caractere de tipo identificador.  
  
-   **Tipo de estrutura.** Não há nenhum tipo correspondente no .NET Framework. Todas as estruturas herdam da classe do .NET Framework <xref:System.ValueType?displayProperty=fullName>, mas nenhuma estrutura individual corresponde ao <xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName>  
  
## <a name="example"></a>Exemplo  
 O paradigma do seguinte mostra a estrutura da declaração de uma estrutura.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ValueType></xref:System.ValueType>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute></xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
