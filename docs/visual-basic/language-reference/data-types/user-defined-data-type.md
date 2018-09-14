---
title: Tipo de dados definido pelo usuário (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- UserDefined
- UDT
- vb.UDT
- User-Defined
- vb.UserDefined
- vb.User-Defined
helpviewer_keywords:
- user-defined data types [Visual Basic], Visual Basic
- user-defined types
- structures [Visual Basic], as user-defined data types
- user-defined types [Visual Basic], Visual Basic
- user-defined types [Visual Basic], structure declaration
- user-defined types [Visual Basic], structures in Visual Basic
- user-defined data types [Visual Basic], structure declaration
- data types [Visual Basic], assigning
- Structure statement [Visual Basic]
- data types [Visual Basic], user-defined
- user-defined data types [Visual Basic], structures in Visual Basic
- user-defined data types
- types [Visual Basic], user-defined
ms.assetid: be913dca-a364-4a51-96a1-549a1b390b0a
ms.openlocfilehash: 1dac93145b6e11a0d149f03b43e1e0b28b770925
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45509838"
---
# <a name="user-defined-data-type"></a>Tipo de dados definido pelo usuário
Contém os dados em um formato que você definir. O `Structure` instrução define o formato.  
  
 As versões anteriores do Visual Basic suportam o tipo definido pelo usuário (UDT). A versão atual expande o UDT para um *estrutura*. Uma estrutura é uma concatenação de um ou mais *membros* de vários tipos de dados. Visual Basic trata uma estrutura como uma única unidade, embora você também pode acessar seus membros individualmente.  
  
## <a name="remarks"></a>Comentários  
 Definir e usar um tipo de dados de estrutura quando você precisa combinar vários tipos de dados em uma única unidade, ou quando nenhum dos tipos de dados elementares atender às suas necessidades.  
  
 O valor padrão de um tipo de dados de estrutura consiste na combinação dos valores padrão de cada um dos seus membros.  
  
## <a name="declaration-format"></a>Formato de declaração  
 Uma declaração de estrutura começa com o [instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md) e termina com o `End Structure` instrução. O `Structure` instrução fornece o nome da estrutura, que também é o identificador do tipo de dados é que define a estrutura. Outras partes do código podem usar esse identificador para declarar variáveis, parâmetros e função de valores de retorno para ser do tipo de dados dessa estrutura.  
  
 As declarações entre o `Structure` e `End Structure` instruções definem os membros da estrutura.  
  
## <a name="member-access-levels"></a>Níveis de acesso de membro  
 Você deve declarar cada membro usando um [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md) ou uma declaração que especifica o nível de acesso, como [pública](../../../visual-basic/language-reference/modifiers/public.md), [amigo](../../../visual-basic/language-reference/modifiers/friend.md), ou [privada](../../../visual-basic/language-reference/modifiers/private.md). Se você usar um `Dim` instrução, os padrões de nível de acesso para público.  
  
## <a name="programming-tips"></a>Dicas de programação  
  
-   **Consumo de memória.** Assim como acontece com todos os tipos de dados compostos, você não pode calcular com segurança o consumo de memória total de uma estrutura somando as alocações de armazenamento nominais de seus membros. Além disso, você não pode presumir com segurança que a ordem de armazenamento na memória é a mesma que sua ordem de declaração. Se você precisar controlar o layout de armazenamento de uma estrutura, você pode aplicar a <xref:System.Runtime.InteropServices.StructLayoutAttribute> de atributo para o `Structure` instrução.  
  
-   **Considerações de interoperabilidade.** Se você estiver fazendo interface com componentes não escritos para o .NET Framework, por exemplo objetos de automação ou COM, lembre-se de que os tipos definidos pelo usuário em outros ambientes não são compatíveis com o Visual Basic estruturam tipos.  
  
-   **Ampliação.** Não há nenhuma conversão automática de ou para qualquer tipo de dados de estrutura. Você pode definir operadores de conversão em sua estrutura usando o [instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md), e você pode declarar cada operador de conversão para ser `Widening` ou `Narrowing`.  
  
-   **Caracteres de tipo.** Tipos de dados de estrutura não têm nenhum caractere de tipo literal ou um caractere de tipo identificador.  
  
-   **Tipo de estrutura.** Não há nenhum tipo correspondente no .NET Framework. Todas as estruturas herdam da classe do .NET Framework <xref:System.ValueType?displayProperty=nameWithType>, mas nenhuma estrutura individual corresponde ao <xref:System.ValueType?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemplo  
 O paradigma a seguir mostra a estrutura da declaração de uma estrutura.  
  
```  
[Public | Protected | Friend | Protected Friend | Private] Structure structname  
    {Dim | Public | Friend | Private} member1 As datatype1  
    ' ...  
    {Dim | Public | Friend | Private} memberN As datatypeN  
End Structure  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ValueType>  
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>  
 [Tipos de Dados](../../../visual-basic/language-reference/data-types/index.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Ampliação](../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
