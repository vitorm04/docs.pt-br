---
title: Declarar Statement (Visual Basic)
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
ms.openlocfilehash: 4a2e1704e72e608f5b5fd9c6dace42c144f92bb4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973165"
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
|`attributelist`|Opcional. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional. Pode ser uma das seguintes opções:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privado](../../../visual-basic/language-reference/modifiers/private.md)<br />- [Friend protegido](../../language-reference/modifiers/protected-friend.md)<br />- [Privado protegido](../../language-reference/modifiers/private-protected.md)<br /><br /> Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional. Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Opcional. Especifica o conjunto de caracteres e o arquivo de informações de pesquisa. Pode ser uma das seguintes opções:<br /><br /> -   [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md) (padrão)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Automático](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|Opcional, mas qualquer um `Sub` ou `Function` deve aparecer. Indica que o procedimento externo não retorna um valor.|  
|`Function`|Opcional, mas qualquer um `Sub` ou `Function` deve aparecer. Indica que o procedimento externo retorna um valor.|  
|`name`|Necessário. Nome dessa referência externa. Para obter mais informações, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Necessário. Apresenta um `Lib` cláusula, que identifica o arquivo externo (DLL ou recurso de código) que contém um procedimento externo.|  
|`libname`|Necessário. Nome do arquivo que contém o procedimento declarado.|  
|`Alias`|Opcional. Indica que o procedimento que está sendo declarado não pode ser identificado em seu arquivo pelo nome especificado em `name`. Você especifica sua identificação em `aliasname`.|  
|`aliasname`|Necessário se você usar o `Alias` palavra-chave. Cadeia de caracteres que identifica o procedimento em uma das duas maneiras:<br /><br /> O nome do ponto de entrada do procedimento em seu arquivo, dentro de aspas (`""`)<br /><br /> -ou-<br /><br /> Um sinal numérico (`#`) seguido por um inteiro que especifica o número ordinal do ponto de entrada do procedimento em seu arquivo|  
|`parameterlist`|Necessário se o procedimento usa parâmetros. Ver [lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Necessário se `Function` for especificado e `Option Strict` é `On`. Tipo de dados do valor retornado pelo procedimento.|  
  
## <a name="remarks"></a>Comentários  
 Às vezes, você precisa chamar um procedimento definido em um arquivo (como um recurso de código ou DLL) fora do seu projeto. Quando você fizer isso, o compilador do Visual Basic não tem acesso a informações necessárias para chamar o procedimento corretamente, como onde o procedimento está localizado, como ele é identificado, sua sequência de chamada e tipo de retorno e o conjunto de caracteres de cadeia de caracteres que ele usa. O `Declare` instrução cria uma referência a um procedimento externo e fornece esta informação necessária.  
  
 Você pode usar `Declare` apenas no nível de módulo. Isso significa que o *contexto de declaração* para uma referência externa deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace, interface, procedimento ou bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Externa faz referência padrão para [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso. Você pode ajustar os níveis de acesso com os modificadores de acesso.  
  
## <a name="rules"></a>Regras  
  
-   **Atributos.** Você pode aplicar atributos para uma referência externa. Qualquer atributo que você aplique tem efeito somente no seu projeto, não no arquivo externo.  
  
-   **Modificadores.** Procedimentos externos são implicitamente [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md). Não é possível usar o `Shared` palavra-chave quando declarar uma referência externa e não é possível alterar seu status compartilhado.  
  
     Um procedimento externo não pode participar de substituição, implementar membros de interface ou manipular eventos. Da mesma forma, você não pode usar o `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, ou `Handles` palavra-chave em um `Declare` instrução.  
  
-   **Nome do procedimento externo.** Você não precisa atribuir esta referência externa o mesmo nome (no `name`) como o nome do ponto de entrada do procedimento em seu arquivo externo (`aliasname`). Você pode usar um `Alias` cláusula para especificar o nome do ponto de entrada. Isso pode ser útil se o procedimento externo tem o mesmo nome como um modificador reservado do Visual Basic ou uma variável, procedimento ou qualquer outro elemento de programação no mesmo escopo.  
  
    > [!NOTE]
    >  Nomes de ponto de entrada na maioria das DLLs diferenciam maiusculas de minúsculas.  
  
-   **Número do procedimento externo.** Como alternativa, você pode usar um `Alias` cláusula para especificar o número ordinal do ponto de entrada dentro da tabela de exportação de arquivo externo. Para fazer isso, você deve começar `aliasname` com um sinal numérico (`#`). Isso pode ser útil se qualquer caractere no nome do procedimento externo não é permitido no Visual Basic, ou se o arquivo externo exporta o procedimento sem um nome.  
  
## <a name="data-type-rules"></a>Regras de tipo de dados  
  
-   **Tipos de dados do parâmetro.** Se `Option Strict` está `On`, você deve especificar o tipo de dados de cada parâmetro em `parameterlist`. Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface. Dentro de `parameterlist`, você usa um `As` cláusula para especificar o tipo de dados do argumento a ser passado para cada parâmetro.  
  
    > [!NOTE]
    >  Se o procedimento externo não tenha sido escrito para o .NET Framework, você deve observar que correspondem os tipos de dados. Por exemplo, se você declarar uma referência externa para um procedimento do Visual Basic 6.0 com um `Integer` parâmetro (16 bits no Visual Basic 6.0), você deve identificar o argumento correspondente como `Short` no `Declare` instrução, pois é 16 - tipo de inteiro do bit no Visual Basic. Da mesma forma, `Long` tem uma largura de dados diferente no Visual Basic 6.0, e `Date` é implementado de maneira diferente.  
  
-   **Retorne o tipo de dados.** Se o procedimento externo é uma `Function` e `Option Strict` é `On`, você deve especificar o tipo de dados do valor retornado para o código de chamada. Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
    > [!NOTE]
    >  O compilador do Visual Basic não verifica se os tipos de dados são compatíveis com aqueles do procedimento externo. Se houver uma incompatibilidade, o common language runtime gerará uma <xref:System.Runtime.InteropServices.MarshalDirectiveException> exceção em tempo de execução.  
  
-   **Tipos de dados padrão.** Se `Option Strict` está `Off` e você não especificar o tipo de dados de um parâmetro na `parameterlist`, o compilador do Visual Basic converte o argumento correspondente para o [tipo de dados do objeto](../../../visual-basic/language-reference/data-types/object-data-type.md). Da mesma forma, se você não especificar `returntype`, o compilador usa o tipo de dados de retorno seja `Object`.  
  
    > [!NOTE]
    >  Como você está lidando com um procedimento externo que pode ter sido gravado em uma plataforma diferente, é perigoso fazer suposições sobre os tipos de dados ou para permitir que sejam padrão. É muito mais seguro especificar o tipo de dados de cada parâmetro e do valor de retorno, se houver. Isso também melhora a legibilidade do código.  
  
## <a name="behavior"></a>Comportamento  
  
-   **Escopo.** Uma referência externa está no escopo em toda a sua classe, estrutura ou módulo.  
  
-   **Tempo de vida.** Uma referência externa tem a mesma duração de classe, estrutura ou módulo no qual ela é declarada.  
  
-   **Chamando um procedimento externo.** Você chama um procedimento externo da mesma maneira que você chamar um `Function` ou `Sub` procedimento — ao usá-lo em uma expressão, se ele retorna um valor, ou especificando-o em uma [instrução Call](../../../visual-basic/language-reference/statements/call-statement.md) se ele não retorna um valor.  
  
     Passar argumentos para o procedimento externo exatamente conforme especificado por `parameterlist` no `Declare` instrução. Não levam em conta como os parâmetros foram originalmente declarados no arquivo externo. Da mesma forma, se houver um valor de retorno, use-o exatamente conforme especificado por `returntype` no `Declare` instrução.  
  
-   **Conjuntos de caracteres.** Você pode especificar no `charsetmodifier` como Visual Basic deve realizar marshaling de cadeias de caracteres quando ele chama o procedimento externo. O `Ansi` direciona o modificador de Visual Basic para realizar marshaling de todas as cadeias de caracteres para valores ANSI e o `Unicode` modificador o direciona para realizar marshaling de todas as cadeias de caracteres para valores Unicode. O `Auto` direciona o modificador de Visual Basic para empacotar cadeias de caracteres de acordo com o .NET Framework de regras com base em referência externa `name`, ou `aliasname` se especificado. O valor padrão é `Ansi`.  
  
     `charsetmodifier` também especifica como Visual Basic deve consultar o procedimento externo em seu arquivo externo. `Ansi` e `Unicode` ambos direcionam o Visual Basic para pesquisar sem modificar seu nome durante a pesquisa. `Auto` direciona o Visual Basic para determinar o conjunto de caracteres base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo, da seguinte maneira:  
  
    -   Em uma plataforma de ANSI, como o Windows 95, Windows 98 ou Windows Millennium Edition, primeiro consultar o procedimento externo sem modificação do nome. Se isso falhar, acrescentar "A" ao final do nome do procedimento externo e procurá-lo novamente.  
  
    -   Em uma plataforma Unicode, como Windows NT, Windows 2000 ou Windows XP, primeiro consultar o procedimento externo sem modificação do nome. Se isso falhar, acrescente "W" ao final do procedimento externo nomear e procurá-lo novamente.  
  
-   **Mecanismo.** Visual Basic usa o .NET Framework *de invocação de plataforma* mecanismo (PInvoke) para resolver e acessar procedimentos externos. O `Declare` instrução e o <xref:System.Runtime.InteropServices.DllImportAttribute> classe os dois usam este mecanismo automaticamente e não é necessário nenhum conhecimento do PInvoke. Para obter mais informações, confira [Passo a passo: Chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Se o procedimento externo é executado fora o common language runtime (CLR), vale *código não gerenciado*. Quando você chama tal procedimento, por exemplo, uma função de API do Win32 ou um método COM, você pode expor seu aplicativo a riscos de segurança. Para obter mais informações, consulte [diretrizes de codificação segura para código não gerenciado](../../../framework/security/secure-coding-guidelines-for-unmanaged-code.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara uma referência externa para uma `Function` procedimento que retorna o nome de usuário atual. Depois, ele chama o procedimento externo `GetUserNameA` como parte do `getUser` procedimento.  
  
 [!code-vb[VbVbalrStatements#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#15)]  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Runtime.InteropServices.DllImportAttribute> fornece uma maneira alternativa de usar funções em código não gerenciado. O exemplo a seguir declara uma função importada sem usar um `Declare` instrução.  
  
 [!code-vb[VbVbalrStatements#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#16)]  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Instrução Imports (Tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Lista de Parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)
- [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Passo a passo: fazer chamadas de APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
