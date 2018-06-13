---
title: Instrução Option Strict
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: de9703c43d32fba4a5f9d661546e0beb66c24602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605349"
---
# <a name="option-strict-statement"></a>Instrução Option Strict
Restringe conversões de tipo de dados implícitos para somente conversões de expansão, não permite associação tardia e não permite digitar implícita que resulta em um `Object` tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`On`|Opcional. Permite `Option Strict` verificação.|  
|`Off`|Opcional. Desabilita `Option Strict` verificação.|  
  
## <a name="remarks"></a>Comentários  
 Quando `Option Strict On` ou `Option Strict` aparece em um arquivo, as seguintes condições causar um erro de tempo de compilação:  
  
-   Conversões de estreitamento implícitas  
  
-   Associação tardia  
  
-   Digitação implícita que resulta em um tipo `Object`  
  
> [!NOTE]
>  Nas configurações de aviso que você pode definir o [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), há três configurações que correspondem às três condições que causam um erro de tempo de compilação. Para obter informações sobre como usar essas configurações, consulte [para definir configurações de aviso no IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) mais adiante neste tópico.  
  
 O `Option Strict Off` instrução desativa o erro e aviso de verificação para todas as três condições, mesmo que especificarem as configurações de IDE associadas para ativar esses erros ou avisos. O `Option Strict On` instrução ativa de erro e aviso de verificação para todas as três condições, mesmo que especificarem as configurações de IDE associadas para desativar esses erros ou avisos.  
  
 Se usado, o `Option Strict` a instrução deve aparecer antes de quaisquer outras instruções de código em um arquivo.  
  
 Quando você define `Option Strict` para `On`, Visual Basic verifica se os tipos de dados são especificados para todos os elementos de programação. Tipos de dados podem ser especificados explicitamente, ou especificados usando inferência de tipo local. Especificando tipos de dados para todos os elementos de programação é recomendado, pelos seguintes motivos:  
  
-   Ele permite o suporte ao IntelliSense para suas variáveis e parâmetros. Isso permite que você veja suas propriedades e outros membros conforme você digita o código.  
  
-   Ele permite que o compilador realizar a verificação de tipo. Verificação de tipo ajuda você a encontrar instruções que podem falhar em tempo de execução devido a erros de conversão de tipo. Ele também identifica chamadas para métodos em objetos que não dão suporte a esses métodos.  
  
-   Acelera a execução de código. Uma razão para isso é que se você não especificar um tipo de dados para um elemento de programação, o compilador do Visual Basic atribui o `Object` tipo. Código compilado pode precisar converter entre `Object` e outros tipos de dados, o que reduz o desempenho.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Erros de conversão de estreitamento implícitas  
 Erros de conversão de redução implícita ocorrerem quando há uma conversão de tipo de dados implícita que é uma conversão de redução.  
  
 Visual Basic pode converter muitos tipos de dados para outros tipos de dados. Pode ocorrer perda de dados quando o valor de um tipo de dados é convertido em um tipo de dados que tem menos precisão ou capacidade menor. Ocorrerá um erro de tempo de execução se tal conversão de restrição falhar. `Option Strict` garante a notificação de tempo de compilação dessas conversões de estreitamento para que você pode evitá-los. Para obter mais informações, consulte [conversões explícitas e implícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) e [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Conversões que podem causar erros incluem conversões implícitas que ocorrem em expressões. Para mais informações, consulte os seguintes tópicos:  
  
-   [Operador +](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
-   [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
-   [\ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
-   [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
-   [Tipo de Dados de Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 Quando você concatenar cadeias de caracteres usando o [& operador](../../../visual-basic/language-reference/operators/concatenation-operator.md), todas as conversões para as cadeias de caracteres são consideradas ser ampliação. Portanto, essas conversões não gerar um erro de conversão de estreitamento implícitas, mesmo se `Option Strict` está em.  
  
 Quando você chama um método que tem um argumento que tem um tipo de dados diferente do parâmetro correspondente, uma conversão de restrição causará um erro de tempo de compilação se `Option Strict` está em. Você pode evitar o erro de tempo de compilação usando uma conversão de ampliação ou uma conversão explícita.  
  
 Erros de conversão de estreitamento implícitas são suprimidos no tempo de compilação para conversões de elementos em um `For Each…Next` coleção para a variável de controle de loop. Isso ocorre mesmo se `Option Strict` está em. Para obter mais informações, consulte a seção "Conversões de estreitamento" [para cada um... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Erros de associação tardia  
 Um objeto tem associação tardia quando é atribuído a uma propriedade ou a um método de uma variável declarada como sendo do tipo `Object`. Para obter mais informações, consulte [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Erros de tipo de objeto implícito  
 Erros de tipo de objeto implícitos ocorrem quando um tipo apropriado não pode ser inferido de uma variável declarada, portanto, um tipo de `Object` é inferido. Isso ocorre principalmente quando você usa uma instrução `Dim` para declarar uma variável sem usar uma cláusula `As` e `Option Infer` está desativado. Para obter mais informações, consulte [opção Infer instrução](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).  
  
 Para parâmetros de método, o `As` cláusula é opcional se `Option Strict` está desativado. No entanto, se qualquer outro parâmetro usa um `As` cláusula, todos eles devem usá-la. Se `Option Strict` está ativada, o `As` cláusula é necessária para cada definição de parâmetro.  
  
 Se você declarar uma variável sem usar um `As` cláusula e defina-a como `Nothing`, a variável tem um tipo de `Object`. Nesse caso não ocorre nenhum erro de tempo de compilação quando `Option Strict` está em e `Option Infer` está em. Um exemplo disso é `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>Tipos de Dados e Valores Padrão  
 A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e um inicializador em uma [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|Tipo de dados especificado?|Inicializador especificado?|Exemplo|Resultado|  
|---|---|---|---|  
|Não|Não|`Dim qty`|Se o `Option Strict` estiver desativado (padrão), a variável é definida como `Nothing`.<br /><br /> Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Não|Sim|`Dim qty = 5`|Se `Option Infer` estiver ativado (padrão), a variável usa o tipo de dados do inicializador. Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Sim|Não|`Dim qty As Integer`|A variável é inicializada para o valor padrão para o tipo de dados. Para obter mais informações, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|Sim|Sim|`Dim qty  As Integer = 5`|Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Quando uma instrução Option Strict não está presente  
 Se o código-fonte não contém um `Option Strict` instrução, o **opção strict** definição no [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) é usado. O **página Compile** tem configurações que fornecem controle adicional sobre as condições que geram um erro.  
  
 Se você estiver usando o compilador de linha de comando, você pode usar o [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador para especificar uma configuração para `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>Para definir o Option Strict no IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1.  No **Gerenciador de Soluções**, selecione um projeto. No menu **Projeto**, clique em **Propriedades**.  
  
2.  No **compilar** guia, defina o valor **Option Strict** caixa.  
  
###  <a name="conditions"></a> Para definir configurações de aviso no IDE  
 Quando você usa o [página de compilação, Designer de projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) em vez de um `Option Strict` instrução, você tem mais controle sobre as condições que geram erros. O **configurações de aviso** seção o **página Compile** tem configurações que correspondem às três condições que causam um erro de tempo de compilação quando `Option Strict` está em. A seguir estão estas configurações:  
  
-   **Conversão implícita**  
  
-   **Associação tardia; a chamada poderia falhar no tempo de execução**  
  
-   **Tipo implícito; objeto assumido**  
  
 Quando você define **Opção Estrita** como **Ativada**, todas estas três definições de configuração de aviso são definidas como **Erro**. Quando você define **Opção Estrita** como **Desativada**, todas as três configurações são definidas como **Nenhum**.  
  
 Você pode alterar individualmente cada definição de configuração de aviso como **Nenhum**, **Aviso** ou **Erro**. Se todas as três definições de configuração de aviso estiverem definidas como **Erro**, `On` aparecerá na caixa `Option strict`. Se todas as três estiverem definidas como **Nenhum**, `Off` será exibido nessa caixa. Para qualquer outra combinação dessas configurações, **(personalizado)** será exibido.  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>Definir o Option Strict padrão para novos projetos  
 Quando você cria um projeto, o **Option Strict** definição no **compilar** for definido como o **Option Strict** definindo no **opções** caixa de diálogo.  
  
 Para definir `Option Strict` nessa caixa de diálogo, no **ferramentas** menu, clique em **opções**. Na caixa de diálogo **Opções**, expanda **Projetos e Soluções** e, em seguida, clique em **Padrões de VB**. A configuração inicial padrão na **padrões VB** é `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>Para definir o Option Strict na linha de comando  
 Incluir o [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) opção de compilador no **vbc** comando.  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram os erros de tempo de compilação devidos a conversões de tipo implícitas são conversões de estreitamento. Esta categoria de erros corresponde ao **conversão implícita** condição de **página Compile**.  
  
 [!code-vb[VbVbalrStatements#161](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra um erro de tempo de compilação causado por associação tardia. Esta categoria de erros corresponde ao **atrasada associação; chamada poderá falhar em tempo de execução** condição a **página Compile**.  
  
 [!code-vb[VbVbalrStatements#162](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir demonstram os erros causados por variáveis que são declaradas com um tipo implícito de `Object`. Esta categoria de erros corresponde ao **tipo implícito; object assumido** condição a **página Compile**.  
  
 [!code-vb[VbVbalrStatements#163](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#164](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-strict-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Conversões de Widening e Narrowing](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Como acessar membros de um objeto](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Expressões Inseridas no XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Vinculação tardia em soluções do Office](https://msdn.microsoft.com/library/3xxe951d)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
