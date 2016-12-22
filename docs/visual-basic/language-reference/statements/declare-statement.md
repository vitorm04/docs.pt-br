---
title: "Instru&#231;&#227;o Declare | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Declare"
  - "vb.Lib"
  - "vb.Any"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "palavra-chave Alias"
  - "APIs, declarando funções API"
  - "palavra-chave As, na instrução Declare"
  - "declarações, externo"
  - "declarações, procedimentos"
  - "instrução Declare"
  - "declarando procedimentos, instrução Declare"
  - "DLLs, declarando procedimentos"
  - "referências externas, Visual Basic"
  - "Procedimentos de função, declarando"
  - "funções [Visual Basic], procedimentos de função"
  - "palavra-chave Lib"
  - "invocação de plataforma, referências externas do Visual Basic"
  - "procedimentos, declaration"
  - "procedimentos, externo"
  - "palavra-chave Public, instrução Declare"
  - "recursos [Visual Basic], declarando"
  - "Subprocedimentos, declarações"
  - "código do Visual Basic, Procedimentos de função"
  - "código do Visual Basic, Subprocedimentos"
ms.assetid: d3f21fb0-b804-4c99-97ed-583b23894cf1
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Declare
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara uma referência a um procedimento implementado em um arquivo externo.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Sub ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ]  
' -or-  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Overloads ] _  
Declare [ charsetmodifier ] [ Function ] name Lib "libname" _  
[ Alias "aliasname" ] [ ([ parameterlist ]) ] [ As returntype ]  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attributelist`|Opcional.  Veja [Lista de Atributos](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Opcional.  Pode ser um dos seguintes:<br /><br /> -   [Público](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional.  Acesse [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`charsetmodifier`|Opcional.  Especifica o conjunto de caracteres e o arquivo de informações de pesquisa.  Pode ser um dos seguintes:<br /><br /> -   [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md) \(padrão\)<br />-   [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)<br />-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)|  
|`Sub`|É opcional, mas um `Sub` ou `Function` deve ser exibido.  Indica que o procedimento externo não retornar um valor.|  
|`Function`|É opcional, mas um `Sub` ou `Function` deve ser exibido.  Indica que o procedimento externo retorna um valor.|  
|`name`|Obrigatório.  Nome dessa referência externa.  Para obter mais informações, consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Lib`|Obrigatório.  Apresenta um `Lib` cláusula, que identifica o arquivo externo \(DLL ou recurso de código\) que contém um procedimento externo.|  
|`libname`|Obrigatório.  Nome do arquivo que contém o procedimento declarado.|  
|`Alias`|Opcional.  Indica que o procedimento que está sendo declarado não pode ser identificado em seu arquivo pelo nome especificado em `name`.  Você especifica sua identificação no `aliasname`.|  
|`aliasname`|Exigido se você usar a palavra\-chave `Alias`.  Seqüência de caracteres que identifica o procedimento de duas maneiras:<br /><br /> O nome do ponto de entrada do procedimento em seu arquivo, entre aspas \(`""`\)<br /><br /> \- ou \-<br /><br /> Um sinal numérico \(`#`\) seguido por um inteiro especificando o número ordinal de um ponto de entrada do procedimento dentro de seu arquivo.|  
|`parameterlist`|Necessário se o procedimento usa parâmetros.  Consulte [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`returntype`|Necessário se `Function` for especificado e `Option Strict` é `On`.  Tipo de dados do valor retornado pelo procedimento.|  
  
## Comentários  
 Às vezes você precisa chamar um procedimento definido em um arquivo \(como um DLL ou recurso de código\) fora do seu projeto.  Quando você fizer isso, o compilador Visual Basic não tem acesso às informações necessárias para chamar o procedimento corretamente, como, por exemplo, onde se encontra o procedimento, como é identificado, sua seqüência de chamada e tipo de retorno e o conjunto de caracteres de seqüência de caracteres que ele usa.  O `Declare` instrução cria uma referência a um procedimento externo e fornece essas informações necessárias.  
  
 Você pode usar `Declare` somente no nível de módulo.  Isso significa que o  *o contexto de declaração* para obter uma referência externa deve ser uma classe, estrutura ou módulo e não pode ser o arquivo de origem, espaço para nome, interface, procedimento ou bloco.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Padrão de referências externas [Público](../../../visual-basic/language-reference/modifiers/public.md) acesso.  Você pode ajustar os seus níveis de acesso com os modificadores de acesso.  
  
## Regras  
  
-   **Atributos.** Você pode aplicar atributos a uma referência externa.  Qualquer atributo que aplicar tem efeito somente no seu projeto, e não no arquivo externo.  
  
-   **Modificador.** Procedimentos externos são implicitamente [Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  Não é possível usar o `Shared` palavra\-chave quando declarar uma referência externa e você não pode alterar seu status compartilhada.  
  
     Um procedimento externo não é possível participar substituindo, implementar membros de interface ou manipular eventos.  Accordingly, you cannot use the `Overrides`, `Overridable`, `NotOverridable`, `MustOverride`, `Implements`, or `Handles` keyword in a `Declare` statement.  
  
-   **Nome do procedimento externo.** Não é necessário dar esta referência externa o mesmo nome \(em `name`\) como nome de ponto de entrada do procedimento em seu arquivo externo \(`aliasname`\).  Você pode usar um `Alias` cláusula para especificar o nome do ponto de entrada.  Isso pode ser útil se o procedimento externo tem o mesmo nome como um modificador de Visual Basic reservado ou uma variável, procedimento ou qualquer outro elemento de programação no mesmo escopo.  
  
    > [!NOTE]
    >  Nomes de ponto de entrada na maioria das DLLs diferenciam maiúsculas de minúsculas.  
  
-   **Número do procedimento externo.** Como alternativa, você pode usar um `Alias` cláusula para especificar o número ordinal de um ponto de entrada dentro da tabela de exportação do arquivo externo.  Para fazer isso, primeiro `aliasname` com um sinal numérico \(`#`\).  Isso pode ser útil se qualquer caractere no nome do procedimento externo não é permitido em Visual Basic, ou se o arquivo externo exporta o procedimento sem um nome.  
  
## Regras de Tipo de Dados  
  
-   **Tipos de dados de parâmetro.** Se `Option Strict` é `On`, você deve especificar o tipo de dados de cada parâmetro na `parameterlist`.  Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  Dentro de `parameterlist`, você pode usar um `As` cláusula para especificar o tipo de dados do argumento a ser passada para cada parâmetro.  
  
    > [!NOTE]
    >  Se o procedimento externo não foi escrito para o.NET Framework, você deve observar que os tipos de dados correspondem.  Por exemplo, se você declarar uma referência externa para um procedimento 6.0 Visual Basic com um `Integer` parâmetro \(16 bits no Visual Basic 6.0\), você deve identificar o argumento correspondente como `Short` na `Declare` instrução, pois é o tipo inteiro de 16 bits em Visual Basic.  Da mesma forma, `Long` tem uma largura de dados diferentes no Visual Basic 6.0, e `Date` é implementada de forma diferente.  
  
-   **Tipo de dados de retorno.** Se o procedimento externo é um `Function` e `Option Strict` é `On`, você deve especificar o tipo de dados do valor retornado para o código de chamada.  Isso pode ser qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
    > [!NOTE]
    >  O compilador Visual Basic não verifica se os seus tipos de dados são compatíveis com aqueles do procedimento externo.  Se houver uma incompatibilidade, o common language runtime gera uma <xref:System.Runtime.InteropServices.MarshalDirectiveException> exceção em tempo de execução.  
  
-   **Tipos de dados padrão.** Se `Option Strict` é `Off` e você não especifica o tipo de dados de um parâmetro no `parameterlist`, o compilador Visual Basic converte o argumento correspondente para o [Tipo de dados Object](../../../visual-basic/language-reference/data-types/object-data-type.md).  Da mesma forma, se você não especificar `returntype`, o compilador usa o tipo de retorno de dados a ser `Object`.  
  
    > [!NOTE]
    >  Porque você está lidando com um procedimento externo que talvez tenha sido escrito em uma plataforma diferente, ele é perigoso para fazer suposições sobre tipos de dados ou para permitir que eles padrão.  É muito mais seguro especificar o tipo de dados de cada parâmetro e o valor de retorno, se houver.  Isso também melhora a legibilidade do código.  
  
## Comportamento  
  
-   **Escopo.** Uma referência externa está no escopo em toda a sua classe, estrutura ou módulo.  
  
-   **Tempo de vida.** Uma referência externa tem o mesmo tempo de vida como a classe, estrutura ou módulo no qual é declarada.  
  
-   **Chamando um procedimento externo.** Você chamar um procedimento externo da mesma maneira que você chamar um `Function` ou `Sub` procedimento — usando\-o em uma expressão se ele retorna um valor, ou especificando\-o em um [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md) se ele não retornar um valor.  
  
     Passar argumentos para o procedimento externo exatamente conforme especificado pelo `parameterlist` na `Declare` instrução.  Não leve em consideração como os parâmetros originalmente foram declarados no arquivo externo.  Da mesma forma, se houver um valor de retorno, usá\-lo exatamente como especificado pelo `returntype` na `Declare` instrução.  
  
-   **Conjuntos de caracteres.** Você pode especificar em `charsetmodifier` como Visual Basic deve empacotar strings quando chama o procedimento externo.  O `Ansi` Visual Basic para empacotar todas as seqüências de caracteres em valores ANSI, direciona o modificador e o `Unicode` modificador direciona para empacotar todas as seqüências de valores Unicode.  O `Auto` Visual Basic direciona o modificador para empacotar seqüências de caracteres de acordo com.NET Framework regras com base na referência externa `name`, ou `aliasname` se especificado.  O valor padrão é `Ansi`.  
  
     `charsetmodifier`também especifica a aparência de Visual Basic o procedimento externo em seu arquivo externo.  `Ansi`e `Unicode` conexão direta de Visual Basic procurá\-lo sem modificar seu nome durante a pesquisa.  `Auto`direciona o Visual Basic para determinar o conjunto de caracteres base da plataforma de tempo de execução e possivelmente modificar o nome do procedimento externo, da seguinte maneira:  
  
    -   Em uma plataforma ANSI, como, por exemplo, Windows 95, Windows 98 ou Windows Millennium Edition, primeiro procure o procedimento externo com nenhuma modificação do nome.  Se isso falhar, acrescentar "A" ao final do nome do procedimento externo e procurá\-lo novamente.  
  
    -   Em uma plataforma Unicode, como, por exemplo, Windows NT, Windows 2000 ou Windows XP, pesquise primeiro o procedimento externo com nenhuma modificação do nome.  Se isso falhar, acrescentar "W" ao final do procedimento externo nome e procurá\-lo novamente.  
  
-   **Mecanismo.** Visual Basic usa o.NET Framework  *de invocação de plataforma* \(PInvoke\) mecanismo para resolver e acessar procedimentos externos.  O `Declare` declaração e a <xref:System.Runtime.InteropServices.DllImportAttribute> classe tanto usar esse mecanismo automaticamente e não é necessário qualquer conhecimento de PInvoke.  Para obter mais informações, consulte [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).  
  
> [!IMPORTANT]
>  Se o procedimento externo é executado fora o common language runtime \(CLR\), é  *código não gerenciado*.  Quando você chamar tal um procedimento, por exemplo, uma função da API do Win32 ou um método COM, você poderá expor seu aplicativo para riscos de segurança.  Para obter mais informações, consulte [Diretrizes de codificação segura para código não gerenciado](../Topic/Secure%20Coding%20Guidelines%20for%20Unmanaged%20Code.md).  
  
## Exemplo  
 O exemplo a seguir declara uma referência externa para um `Function` procedimento que retorna o nome do usuário atual.  Ele chama o procedimento externo `GetUserNameA` como parte do `getUser` procedimento.  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/declare-statement_1.vb)]  
  
## Exemplo  
 O <xref:System.Runtime.InteropServices.DllImportAttribute> fornece uma maneira alternativa de usar funções em código não gerenciado.  O exemplo a seguir declara uma função importada sem usar um `Declare` instrução.  
  
 [!code-vb[VbVbalrStatements#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/declare-statement_2.vb)]  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/declare-statement_3.vb)]  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Lista de parâmetros](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Instrução Call](../../../visual-basic/language-reference/statements/call-statement.md)   
 [Instruções passo a passo: chamando APIs do Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)