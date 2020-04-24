---
title: Instrução Declare
ms.date: 07/20/2015
f1_keywords:
- vb.Declare
- vb.Lib
- vb.Any
helpviewer_keywords:
- Lib keyword [Visual Basic]
- declaring procedures [Visual Basic], Declare statement
- functions [Visual Basic], function procedures
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- procedures [Visual Basic], external
- Alias keyword [Visual Basic]
- external references [Visual Basic], Visual Basic
- DLLs, declaring procedures
- Declare statement [Visual Basic]
- declarations [Visual Basic], external
- Visual Basic code, Function procedures
- As keyword [Visual Basic], in Declare statement
- resources [Visual Basic], declaring
- Public keyword [Visual Basic], Declare statement
- platform invoke, Visual Basic external references
- Sub procedures [Visual Basic], declarations
- APIs, declaring API functions
- Visual Basic code, Sub procedures
- Function procedures [Visual Basic], declaring
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
ms.openlocfilehash: 9895709076634ce156ba9d1009f79ba7ddd2ba56
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646377"
---
# <a name="declare-statement"></a>Instrução Declare

Declara uma referência a um procedimento implementado em um arquivo externo.

## <a name="syntax"></a>Sintaxe

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ]
' -or-
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]
```

## <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|`attributelist`|Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|
|`accessmodifier`|Opcional. Um dos seguintes pode ser feito:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Amigo](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Amigo Protegido](../../language-reference/modifiers/protected-friend.md)<br />- [Soldado Protegido](../../language-reference/modifiers/private-protected.md)<br /><br /> Consulte [os níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|
|`Shadows`|Opcional. Ver [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|
|`charsetmodifier`|Opcional. Especifica o conjunto de caracteres e as informações de pesquisa de arquivos. Um dos seguintes pode ser feito:<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) (padrão)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automático](../../../visual-basic/language-reference/modifiers/auto.md)|
|`Sub`|Opcional, mas `Sub` `Function` ou deve aparecer. Indica que o procedimento externo não retorna um valor.|
|`Function`|Opcional, mas `Sub` `Function` ou deve aparecer. Indica que o procedimento externo retorna um valor.|
|`name`|Obrigatórios. Nome desta referência externa. Para obter mais informações, consulte [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|
|`Lib`|Obrigatórios. Introduz uma `Lib` cláusula, que identifica o arquivo externo (DLL ou recurso de código) que contém um procedimento externo.|
|`libname`|Obrigatórios. Nome do arquivo que contém o procedimento declarado.|
|`Alias`|Opcional. Indica que o procedimento que está sendo declarado não pode `name`ser identificado dentro de seu arquivo pelo nome especificado em . Você especifica sua `aliasname`identificação em .|
|`aliasname`|Necessário se você `Alias` usar a palavra-chave. String que identifica o procedimento de duas maneiras:<br /><br /> O nome do ponto de entrada do procedimento`""`dentro de seu arquivo, dentro das citações ( )<br /><br /> -ou-<br /><br /> Um sinal`#`numérico () seguido de um inteiro especificando o número ordinal do ponto de entrada do procedimento em seu arquivo|
|`parameterlist`|Necessário se o procedimento tomar parâmetros. Ver [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|
|`returntype`|Necessário `Function` se for `Option Strict` especificado e for `On`. Tipo de dados do valor devolvido pelo procedimento.|

## <a name="remarks"></a>Comentários

Às vezes, você precisa chamar um procedimento definido em um arquivo (como um DLL ou recurso de código) fora do seu projeto. Quando você faz isso, o compilador Visual Basic não tem acesso às informações que precisa para chamar o procedimento corretamente, como onde o procedimento está localizado, como ele é identificado, sua seqüência de chamadas e tipo de retorno, e o conjunto de caracteres de seqüência que ele usa. A `Declare` declaração cria uma referência a um procedimento externo e fornece essas informações necessárias.

Você só `Declare` pode usar no nível do módulo. Isso significa que o contexto de *declaração* para uma referência externa deve ser uma classe, estrutura ou módulo, e não pode ser um arquivo de origem, namespace, interface, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).

Referências externas padrão ao [acesso público.](../../../visual-basic/language-reference/modifiers/public.md) Você pode ajustar seus níveis de acesso com os modificadores de acesso.

## <a name="rules"></a>Regras

- **Atributos.** Você pode aplicar atributos a uma referência externa. Qualquer atributo que você aplicar tem efeito apenas no seu projeto, não no arquivo externo.

- **Modificadores.** Os procedimentos externos são implicitamente [compartilhados.](../../../visual-basic/language-reference/modifiers/shared.md) Você não `Shared` pode usar a palavra-chave ao declarar uma referência externa e não pode alterar seu status compartilhado.

  Um procedimento externo não pode participar de sobrepor, implementar membros de interface ou lidar com eventos. Assim, você não `Overrides`pode `Overridable` `NotOverridable`usar `MustOverride` `Implements`a `Handles` palavra-chave `Declare` ou palavra-chave em uma declaração.

- **Nome do procedimento externo.** Você não precisa dar a esta referência `name`externa o mesmo nome (in ) como`aliasname`o nome de ponto de entrada do procedimento dentro de seu arquivo externo ( ). Você pode `Alias` usar uma cláusula para especificar o nome do ponto de entrada. Isso pode ser útil se o procedimento externo tiver o mesmo nome de um modificador reserva Visual Basic ou uma variável, procedimento ou qualquer outro elemento de programação no mesmo escopo.

  > [!NOTE]
  > Os nomes de ponto de entrada na maioria das DLLs são sensíveis a maiúsculas e minúsculas.

- **Número do procedimento externo.** Alternativamente, você pode `Alias` usar uma cláusula para especificar o número ordinal do ponto de entrada na tabela de exportação do arquivo externo. Para fazer isso, `aliasname` você começa`#`com um sinal de número ( ). Isso pode ser útil se qualquer caractere no nome do procedimento externo não for permitido no Visual Basic, ou se o arquivo externo exportar o procedimento sem um nome.

## <a name="data-type-rules"></a>Regras do tipo de dados

- **Tipos de dados de parâmetros.** Se `Option Strict` `On`for, você deve especificar o `parameterlist`tipo de dados de cada parâmetro em . Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface. Dentro, `parameterlist`você `As` usa uma cláusula para especificar o tipo de dados do argumento a ser passado para cada parâmetro.

  > [!NOTE]
  > Se o procedimento externo não foi escrito para o Quadro .NET, você deve tomar cuidado para que os tipos de dados correspondam. Por exemplo, se você declarar uma referência externa a `Integer` um procedimento Visual Basic 6.0 com um parâmetro (16 `Short` bits no Visual Basic 6.0), você deve identificar o argumento correspondente como na `Declare` instrução, porque esse é o tipo inteiro de 16 bits no Visual Basic. Da mesma `Long` forma, tem uma largura de dados `Date` diferente no Visual Basic 6.0, e é implementado de forma diferente.

- **Tipo de dados de retorno.** Se o procedimento `Function` externo `Option Strict` `On`for um e for, você deve especificar o tipo de dados do valor retornado ao código de chamada. Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.

  > [!NOTE]
  > O compilador Visual Basic não verifica se seus tipos de dados são compatíveis com os do procedimento externo. Se houver uma incompatibilidade, o tempo de <xref:System.Runtime.InteropServices.MarshalDirectiveException> execução do idioma comum gera uma exceção no tempo de execução.

- **Tipos de dados padrão.** Se `Option Strict` `Off` for e você não especificar o `parameterlist`tipo de dados de um parâmetro em , o compilador Visual Basic converte o argumento correspondente ao [Tipo de Dados de Objeto](../../../visual-basic/language-reference/data-types/object-data-type.md). Da mesma forma, se `returntype`você não especificar, o compilador leva o tipo de dados de retorno para ser `Object`.

  > [!NOTE]
  > Como você está lidando com um procedimento externo que pode ter sido escrito em uma plataforma diferente, é perigoso fazer qualquer suposição sobre os tipos de dados ou permitir que eles sejam padrão. É muito mais seguro especificar o tipo de dados de cada parâmetro e do valor de retorno, se houver. Isso também melhora a legibilidade do seu código.

## <a name="behavior"></a>Comportamento

- **Escopo.** Uma referência externa está em escopo em toda a sua classe, estrutura ou módulo.

- **Vida.** Uma referência externa tem a mesma vida útil da classe, estrutura ou módulo em que é declarada.

- **Chamando um procedimento externo.** Você chama um procedimento externo da `Function` `Sub` mesma maneira que você chama de um ou procedimento — usando-o em uma expressão se ele retornar um valor ou especificando-o em uma [Declaração de Chamada](../../../visual-basic/language-reference/statements/call-statement.md) se ele não retornar um valor.

  Você passa argumentos para o procedimento `parameterlist` externo `Declare` exatamente como especificado na declaração. Não leve em conta como os parâmetros foram originalmente declarados no arquivo externo. Da mesma forma, se houver um valor de `returntype` retorno, `Declare` use-o exatamente como especificado na declaração.

- **Conjuntos de caracteres.** Você pode `charsetmodifier` especificar em como o Visual Basic deve empacotar strings quando ele chama o procedimento externo. O `Ansi` modificador direciona o Visual Basic para empacotar `Unicode` todas as strings para os valores ANSI, e o modificador direciona-o para empacotar todas as strings para valores Unicode. O `Auto` modificador direciona o Visual Basic para as strings marshal `name`de `aliasname` acordo com as regras do .NET Framework com base na referência externa ou se especificado. O valor padrão é `Ansi`.

  `charsetmodifier`também especifica como o Visual Basic deve procurar o procedimento externo dentro de seu arquivo externo. `Ansi`e `Unicode` ambos diretos visual basic para procurá-lo sem modificar seu nome durante a pesquisa. `Auto`direciona o Visual Basic para determinar o conjunto de caracteres base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo, da seguinte forma:

  - Em uma plataforma ANSI, como Windows 95, Windows 98 ou Windows Millennium Edition, primeiro procure o procedimento externo sem modificação de nome. Se isso falhar, apêndice "A" até o final do nome do procedimento externo e procure-o novamente.

  - Em uma plataforma Unicode, como Windows NT, Windows 2000 ou Windows XP, primeiro procure o procedimento externo sem modificação de nome. Se isso falhar, apêndice "W" até o final do nome do procedimento externo e procure-o novamente.

- **Mecanismo.** O Visual Basic usa o mecanismo de *invocação da plataforma* .NET Framework (PInvoke) para resolver e acessar procedimentos externos. A `Declare` declaração <xref:System.Runtime.InteropServices.DllImportAttribute> e a classe usam este mecanismo automaticamente, e você não precisa de nenhum conhecimento do PInvoke. Para obter mais informações, consulte [Passo a Passo: Chamando as APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).

> [!IMPORTANT]
> Se o procedimento externo for executado fora do tempo de execução da linguagem comum (CLR), ele será *um código não gerenciado*. Quando você chama esse procedimento, por exemplo, uma função de API do Windows ou um método COM, você pode expor seu aplicativo a riscos de segurança. Para obter mais informações, consulte [Diretrizes de codificação segura para código não gerenciado](https://docs.microsoft.com/previous-versions/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code).

## <a name="example"></a>Exemplo

O exemplo a seguir declara `Function` uma referência externa a um procedimento que retorna o nome de usuário atual. Em seguida, chama `GetUserNameA` o procedimento `getUser` externo como parte do procedimento.

[!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]

## <a name="example"></a>Exemplo

O <xref:System.Runtime.InteropServices.DllImportAttribute> fornece uma maneira alternativa de usar funções em código não gerenciado. O exemplo a seguir declara uma `Declare` função importada sem o uso de uma declaração.

[!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]

[!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Declaração de função](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Parâmetro](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
