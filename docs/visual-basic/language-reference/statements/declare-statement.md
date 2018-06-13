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
ms.openlocfilehash: 75d41883aefbaa54eb836d89bbfc034d99b7bba0
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233971"
---
# <a name="declare-statement"></a>Instrução Declare
Declara uma referência a um procedimento implementado em um arquivo externo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
|`attributelist`|Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privada](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Friend protegido](../../language-reference/modifiers/protected-friend.md)<br />- [Privado protegido](../../language-reference/modifiers/private-protected.md)<br /><br /> Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Opcional. Especifica o conjunto de caracteres e o arquivo de informações de pesquisa. Pode ser um dos seguintes:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (padrão)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automático](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Opcional, mas o `Sub` ou `Function` devem aparecer. Indica que o procedimento externo não retorna um valor.|  
|`Function`|Opcional, mas o `Sub` ou `Function` devem aparecer. Indica que o procedimento externo retorna um valor.|  
|`name`|Necessário. Nome dessa referência externa. Para obter mais informações, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Necessário. Apresenta um `Lib` cláusula que identifica o arquivo externo (DLL ou recurso de código) que contém um procedimento externo.|  
|`libname`|Necessário. Nome do arquivo que contém o procedimento declarado.|  
|`Alias`|Opcional. Indica que o procedimento está sendo declarado não pode ser identificado em seu arquivo com o nome especificado em `name`. Especifique sua identificação em `aliasname`.|  
|`aliasname`|Necessário se você usar o `Alias` palavra-chave. Cadeia de caracteres que identifica o procedimento de duas maneiras:<br /><br /> O nome do ponto de entrada do procedimento em seu arquivo, entre aspas (`""`)<br /><br /> -ou-<br /><br /> Um sinal de número (`#`) seguido por um inteiro que especifica o número ordinal do ponto de entrada do procedimento em seu arquivo|  
|`parameterlist`|Necessário se o procedimento usa parâmetros. Consulte [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Necessário se `Function` for especificado e `Option Strict` é `On`. Tipo de dados do valor retornado pelo procedimento.|  
  
## <a name="remarks"></a>Comentários  
 Às vezes você precisa chamar um procedimento definido em um arquivo (como um DLL ou recurso de código) fora do seu projeto. Quando você fizer isso, o compilador do Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente, como onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres de cadeia de caracteres que ele usa. O `Declare` instrução cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 Você pode usar `Declare` apenas no nível de módulo. Isso significa que o *contexto declaração* para uma referência externa deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace, interface, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Externa referencia padrão [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso.  
  
## <a name="rules"></a>Regras  
  
-   **Atributos.** Você pode aplicar atributos a uma referência externa. Qualquer atributo que você aplicar tem efeito somente no seu projeto, não no arquivo externo.  
  
-   **Modificadores.** Procedimentos externos são implicitamente [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md). Não é possível usar o `Shared` palavra-chave quando declarando uma referência externa e você não pode alterar seu status compartilhado.  
  
     Um procedimento externo não pode participar de substituição, implementar membros de interface ou manipular eventos. Da mesma forma, você não pode usar o `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, ou `Handles` palavra-chave em um `Declare` instrução.  
  
-   **Nome do procedimento externo.** Não é necessário atribuir o mesmo nome esta referência externa (em `name`) como o nome do ponto de entrada do procedimento em seu arquivo externo (`aliasname`). Você pode usar um `Alias` cláusula para especificar o nome do ponto de entrada. Isso pode ser útil se o procedimento externo tem o mesmo nome como um modificador reservado do Visual Basic ou uma variável, procedimento ou qualquer outro elemento de programação no mesmo escopo.  
  
    > [!NOTE]
    >  Nomes de ponto de entrada na maioria das DLLs diferenciam maiusculas de minúsculas.  
  
-   **Número do procedimento externo.** Como alternativa, você pode usar um `Alias` cláusula para especificar o número ordinal do ponto de entrada dentro da tabela de exportação de arquivo externo. Para fazer isso, começar `aliasname` com um sinal numérico (`#`). Isso pode ser útil se qualquer caractere no nome do procedimento externo não é permitido no Visual Basic, ou se o arquivo externo exporta o procedimento sem um nome.  
  
## <a name="data-type-rules"></a>Regras de tipo de dados  
  
-   **Tipos de dados do parâmetro.** Se `Option Strict` é `On`, você deve especificar o tipo de dados de cada parâmetro em `parameterlist`. Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface. Dentro de `parameterlist`, você usa um `As` cláusula para especificar o tipo de dados do argumento a ser passado para cada parâmetro.  
  
    > [!NOTE]
    >  Se o procedimento externo não foi gravado para o .NET Framework, você deve observar que correspondem os tipos de dados. Por exemplo, se você declarar uma referência externa para um procedimento do Visual Basic 6.0 com um `Integer` parâmetro (16 bits no Visual Basic 6.0), você deve identificar o argumento correspondente como `Short` no `Declare` instrução, pois é 16 - tipo de inteiro de bit no Visual Basic. Da mesma forma, `Long` tem uma largura de dados diferente no Visual Basic 6.0, e `Date` é implementado de maneira diferente.  
  
-   **Retorna o tipo de dados.** Se o procedimento externo é uma `Function` e `Option Strict` é `On`, você deve especificar o tipo de dados do valor retornado ao código de chamada. Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
    > [!NOTE]
    >  O compilador do Visual Basic não verifica se os tipos de dados são compatíveis com os do procedimento externo. Se houver uma incompatibilidade, o common language runtime gera um <xref:System.Runtime.InteropServices.MarshalDirectiveException> exceção em tempo de execução.  
  
-   **Tipos de dados padrão.** Se `Option Strict` é `Off` e você não especificar o tipo de dados de um parâmetro em `parameterlist`, o compilador do Visual Basic converte o argumento correspondente para o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md). Da mesma forma, se você não especificar `returntype`, o compilador usa o tipo de dados de retorno para ser `Object`.  
  
    > [!NOTE]
    >  Porque você está lidando com um procedimento externo pode ter sido gravado em uma plataforma diferente, é perigoso para fazer suposições sobre tipos de dados ou para permitir que eles como padrão. É muito mais seguro especificar o tipo de dados de cada parâmetro e o valor de retorno, se houver. Isso também melhora a legibilidade do código.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Escopo.** Uma referência externa está no escopo em toda a sua classe, estrutura ou módulo.  
  
-   **Tempo de vida.** Uma referência externa tem a mesma duração como a classe, estrutura ou módulo no qual ela é declarada.  
  
-   **Chamando um procedimento externo.** Você chamar um procedimento externo da mesma maneira que você chamar um `Function` ou `Sub` procedimento — ao usá-lo em uma expressão, se ele retorna um valor, ou especificando-o em um [instrução Call](../../../visual-basic/language-reference/statements/call-statement.md) se ele não retorna um valor.  
  
     Passar argumentos para o procedimento externo exatamente conforme especificado por `parameterlist` no `Declare` instrução. Não levam em conta como os parâmetros foram originalmente declarados no arquivo externo. Da mesma forma, se houver um valor de retorno, use-o exatamente conforme especificado por `returntype` no `Declare` instrução.  
  
-   **Conjuntos de caracteres.** Você pode especificar em `charsetmodifier` como Visual Basic deve realizar marshaling de cadeias de caracteres quando ele chama o procedimento externo. O `Ansi` modificador direciona o Visual Basic para empacotar todas as cadeias de caracteres para valores ANSI e o `Unicode` modificador direciona realizar marshaling de todas as cadeias de caracteres para valores Unicode. O `Auto` modificador direciona o Visual Basic para empacotar cadeias de caracteres de acordo com o .NET Framework regras com base em referência externa `name`, ou `aliasname` se especificado. O valor padrão é `Ansi`.  
  
     `charsetmodifier` também especifica como Visual Basic deve consultar o procedimento externo em seu arquivo externo. `Ansi` e `Unicode` direta Visual Basic para procurá-lo sem modificar seu nome durante a pesquisa. `Auto` direciona o Visual Basic para determinar o conjunto de caracteres base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo, da seguinte maneira:  
  
    -   Em uma plataforma de ANSI, como Windows 95, Windows 98 ou Windows Millennium Edition, primeiro consultar o procedimento externo sem modificação do nome. Se isso falhar, acrescente "A" ao final do nome do procedimento externo e procurá-lo novamente.  
  
    -   Em uma plataforma de Unicode, como o Windows NT, Windows 2000 ou Windows XP, procure-o procedimento externo sem modificação do nome. Se isso falhar, acrescente "W" ao final do procedimento externo nomear e procurá-lo novamente.  
  
-   **Mecanismo.** Visual Basic usa o .NET Framework *invocação de plataforma* mecanismo (PInvoke) para resolver e acessar procedimentos externos. O `Declare` instrução e <xref:System.Runtime.InteropServices.DllImportAttribute> classe ambos usar esse mecanismo automaticamente e não é necessário qualquer conhecimento de PInvoke. Para obter mais informações, consulte [passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Se o procedimento externo é executado fora o common language runtime (CLR), é *código não gerenciado*. Quando você chamar tal procedimento, por exemplo, uma função de API do Win32 ou um método COM, você poderá expor seu aplicativo quanto a riscos de segurança. Para obter mais informações, consulte [diretrizes de codificação segura para código não gerenciado](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma referência externa para uma `Function` procedimento que retorna o nome do usuário atual. Depois, ele chama o procedimento externo `GetUserNameA` como parte do `getUser` procedimento.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Runtime.InteropServices.DllImportAttribute> fornece uma maneira alternativa de usar funções em código não gerenciado. O exemplo a seguir declara uma função importada sem usar um `Declare` instrução.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Lista de Parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
