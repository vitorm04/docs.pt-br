---
title: Instrução Dim (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: b3384b771748a1f2c9e841407042f81ce6ebe76d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234721"
---
# <a name="dim-statement-visual-basic"></a>Instrução Dim (Visual Basic)
Declara e aloca espaço de armazenamento para uma ou mais variáveis.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a>Partes  
  
-   `attributelist`  
  
     Opcional. Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
-   `accessmodifier`  
  
     Opcional. Pode ser um dos seguintes:  
  
    -   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [Friend protegido](../../language-reference/modifiers/protected-friend.md)
    
    - [Privado protegido](../../language-reference/modifiers/private-protected.md)

     Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `Shared`  
  
     Opcional. Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Static`  
  
     Opcional. Consulte [estático](../../../visual-basic/language-reference/modifiers/static.md).  
  
-   `ReadOnly`  
  
     Opcional. Consulte [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
-   `WithEvents`  
  
     Opcional. Especifica que eles são variáveis de objeto que se referem a instâncias de uma classe que pode gerar eventos. Consulte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).  
  
-   `variablelist`  
  
     Necessário. Lista de variáveis que está sendo declarada nessa instrução.  
  
     `variable [ , variable ... ]`  
  
     Cada `variable` tem a seguinte sintaxe e partes:  
  
     `variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`  
  
    |Parte|Descrição|  
    |---|---|  
    |`variablename`|Necessário. Nome da variável. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
    |`boundslist`|Opcional. Lista de limites de cada dimensão de uma variável de matriz.|  
    |`New`|Opcional. Cria uma nova instância da classe quando o `Dim` instrução é executada.|  
    |`datatype`|Opcional. Tipo de dados da variável.|  
    |`With`|Opcional. Apresenta a lista de inicializador de objeto.|  
    |`propertyname`|Opcional. O nome de uma propriedade na classe você estiver fazendo uma instância do.|  
    |`propinitializer`|Necessário após `propertyname` =. A expressão que é avaliada e atribuída ao nome da propriedade.|  
    |`initializer`|Opcional se `New` não for especificado. Expressão que é avaliada e atribuída à variável quando ela é criada.|  
  
## <a name="remarks"></a>Comentários  
 O compilador do Visual Basic usa o `Dim` instrução para determinar o tipo de dados e outras informações, como o código que pode acessar a variável. O exemplo a seguir declara uma variável para manter uma `Integer` valor.  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 Para um tipo de referência, você deve usar o `New` palavra-chave para criar uma nova instância da classe ou estrutura que é especificada pelo tipo de dados. Se você usar `New`, você não usar uma expressão de inicializador. Em vez disso, você fornecer argumentos, caso sejam necessárias para o construtor da classe da qual você está criando a variável.  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 Você pode declarar uma variável em um procedimento, bloquear, classe, estrutura ou módulo. Você não pode declarar uma variável em um arquivo de origem, namespace ou interface. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Uma variável que é declarada no nível de módulo, fora de qualquer procedimento, é um *variável membro* ou *campo*. Variáveis de membro estão no escopo em toda a sua classe, estrutura ou módulo. Uma variável que é declarada no nível de procedimento é um *variável local*. Variáveis locais estão no escopo somente dentro de seu procedimento ou bloco.  
  
 Os modificadores de acesso a seguir são usados para declarar variáveis fora de um procedimento: `Public`, `Protected`, `Friend`, `Protected Friend`, e `Private`. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 O `Dim` palavra-chave é opcional e geralmente omitido se você especificar qualquer um dos seguintes modificadores: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, ou `WithEvents`.  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 Se `Option Explicit` está on (o padrão), o compilador requer uma declaração para cada variável que você usa. Para obter mais informações, consulte [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md).  
  
## <a name="specifying-an-initial-value"></a>Especificando um valor inicial  
 Você pode atribuir um valor a uma variável quando ela é criada. Para um tipo de valor, você deve usar um *inicializador* para fornecer uma expressão a ser atribuído à variável. A expressão deve ser avaliada como uma constante que pode ser calculada em tempo de compilação.  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 Se um inicializador for especificado e não foi especificado um tipo de dados em um `As` cláusula, *inferência de tipo* é usada para inferir o tipo de dados do inicializador. No exemplo a seguir, ambos `num1` e `num2` são fortemente tipadas como inteiros. Na segunda declaração, a inferência de tipo infere o tipo do valor 3.  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 Inferência de tipo aplica-se no nível do procedimento. Não é aplicável fora de um procedimento em uma classe, estrutura, módulo ou interface. Para obter mais informações sobre a inferência de tipo, consulte [opção Infer instrução](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 Para obter informações sobre o que acontece quando um tipo de dados ou um inicializador não for especificado, consulte [tipos de dados padrão e valores](../../../visual-basic/language-reference/statements/dim-statement.md#default) mais adiante neste tópico.  
  
 Você pode usar um *inicializador de objeto* para declarar as instâncias dos tipos nomeados e anônimos. O código a seguir cria uma instância de um `Student` classe e usa um inicializador de objeto para inicializar as propriedades.  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 Para obter mais informações sobre os inicializadores de objeto, consulte [como: declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), e [tipos anônimos ](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
## <a name="declaring-multiple-variables"></a>Declarando variáveis múltiplas  
 Você pode declarar diversas variáveis em uma declaração, especificando o nome da variável para cada um e após cada nome de matriz com parênteses. Diversas variáveis são separadas por vírgulas.  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 Se você declarar mais de uma variável com um `As` cláusula, você não pode fornecer um inicializador para esse grupo de variáveis.  
  
 Você pode especificar diferentes tipos de dados para variáveis diferentes usando um separado `As` cláusula para cada variável que você declarar. Cada variável tem o tipo de dados especificado no primeiro `As` cláusula encontrados após o seu `variablename` parte.  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a>Matrizes  
 Você pode declarar uma variável para manter uma *matriz*, que pode conter vários valores. Para especificar que uma variável contém uma matriz, siga seu `variablename` imediatamente com parênteses. Para obter mais informações sobre matrizes, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Você pode especificar o limite inferior e superior de cada dimensão de uma matriz. Para fazer isso, inclua um `boundslist` dentro dos parênteses. Para cada dimensão, o `boundslist` Especifica o limite superior e, opcionalmente, o limite inferior. O limite inferior é sempre zero, se você especificar ou não. Cada índice pode variar de zero por meio de seu valor de limite superior.  
  
 As duas instruções a seguir são equivalentes. Cada instrução declara uma matriz de 21 `Integer` elementos. Quando você acessar a matriz, o índice pode variar de 0 a 20.  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 A instrução a seguir declara uma matriz bidimensional de tipo `Double`. A matriz tem 4 linhas (3 + 1) de 6 colunas (5 + 1). Observe que um limite superior representa o maior valor possível para o índice, não o comprimento da dimensão. O comprimento da dimensão é o limite superior mais um.  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 Uma matriz pode ter de 1 a 32 dimensões.  
  
 Você pode deixar todos os limites em branco em uma declaração de matriz. Se você fizer isso, a matriz tem o número de dimensões que você especificar, mas ele não foi inicializado. Ele tem um valor de `Nothing` até que você inicializar pelo menos alguns de seus elementos. O `Dim` instrução deve especificar limites para todas as dimensões ou nenhuma dimensão.  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 Se a matriz tem mais de uma dimensão, você deve incluir vírgulas entre os parênteses para indicar o número de dimensões.  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 Você pode declarar uma *matriz de comprimento zero* declarando uma das dimensões da matriz para ser -1. Uma variável que contém uma matriz de comprimento zero não tem o valor `Nothing`. Matrizes de comprimento zero são necessárias determinadas funções do common language runtime. Se você tentar acessar essa matriz, ocorre uma exceção de tempo de execução. Para obter mais informações, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
 Você pode inicializar os valores de uma matriz, usando um literal de matriz. Para fazer isso, coloque os valores de inicialização com colchetes (`{}`).  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 Para matrizes multidimensionais, a inicialização para cada dimensão separada é colocada entre chaves na dimensão externa. Os elementos são especificados na ordem de linhas principais.  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 Para obter mais informações sobre literais de matriz, consulte [matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
##  <a name="default"></a> Tipos de dados padrão e valores  
 A tabela a seguir descreve os resultados de várias combinações de especificar o tipo de dados e o inicializador em uma instrução `Dim`.  
  
|Tipo de dados especificado?|Inicializador especificado?|Exemplo|Resultado|  
|---|---|---|---|  
|Não|Não|`Dim qty`|Se [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) está desativado (padrão), a variável é definida como `Nothing`.<br /><br /> Se `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Não|Sim|`Dim qty = 5`|Se [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) está on (o padrão), a variável usa os dados de tipo do inicializador. Consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver desativado, a variável usa o tipo de dados do `Object`.<br /><br /> Se `Option Infer` estiver desativado e `Option Strict` estiver ativado, ocorre um erro de tempo de compilação.|  
|Sim|Não|`Dim qty As Integer`|A variável é inicializada para o valor padrão para o tipo de dados. Consulte a tabela mais adiante nesta seção.|  
|Sim|Sim|`Dim qty  As Integer = 5`|Se o tipo de dados do inicializador não for conversível para o tipo de dados especificado, ocorrerá um erro de tempo de compilação.|  
  
 Se você especificar um tipo de dados, mas não especificar um inicializador, Visual Basic inicializa a variável para o valor padrão para seu tipo de dados. A tabela a seguir mostra o padrão de valores de inicialização.  
  
|Tipo de dados|Valor padrão|  
|---|---|  
|Todos os tipos numéricos (incluindo `Byte` e `SByte`)|0|  
|`Char`|0 binário|  
|Todos os tipos de referência (incluindo `Object`, `String`e todas as matrizes)|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|12:00 AM de 1º de janeiro do ano 1 (01/01/0001 12:00:00 AM)|  
  
 Cada elemento de uma estrutura é inicializado como se fosse uma variável separada. Se você declara o comprimento de uma matriz, mas não inicializar seus elementos, cada elemento é inicializado como se fosse uma variável separada.  
  
## <a name="static-local-variable-lifetime"></a>Vida útil variável Local estática  
 Um `Static` variável local tem um tempo de vida mais longo do que o procedimento no qual ela é declarada. Os limites de tempo de vida da variável dependem de onde o procedimento é declarado e se ela é `Shared`.  
  
|Declaração de procedimento|Variável inicializada|Variável interrompe existente|  
|---|---|---|  
|Em um módulo|Na primeira vez em que o procedimento é chamado.|Quando o programa para a execução|  
|Em uma classe ou estrutura, o procedimento é `Shared`|Na primeira vez que o procedimento é chamado em uma instância específica ou na classe ou estrutura em si|Quando o programa para a execução|  
|Em uma classe ou estrutura, o procedimento não é `Shared`|Na primeira vez em que o procedimento é chamado em uma instância específica|Quando a instância é liberada para coleta de lixo (GC)|  
  
## <a name="attributes-and-modifiers"></a>Modificadores e atributos  
 Você pode aplicar atributos apenas para variáveis de membro, não para variáveis locais. Um atributo contribui com informações para metadados do assembly, que não é significativo para armazenamento temporário, como variáveis locais.  
  
 No nível de módulo, você não pode usar o `Static` modificador para declarar variáveis de membro. No nível de procedimento, você não pode usar `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ou qualquer modificador de acesso para declarar variáveis locais.  
  
 Você pode especificar qual código pode acessar uma variável, fornecendo um `accessmodifier`. Classe e o módulo membro padrão de variáveis (fora de qualquer procedimento) para acesso privado e padrão de variáveis de membro de estrutura para acesso público. Você pode ajustar os níveis de acesso com os modificadores de acesso. Você não pode usar os modificadores de acesso em variáveis locais (dentro de um procedimento).  
  
 Você pode especificar `WithEvents` somente em variáveis de membro, não em variáveis locais dentro de um procedimento. Se você especificar `WithEvents`, o tipo de dados da variável deve ser um tipo de classe específica, não `Object`. Você não pode declarar uma matriz com `WithEvents`. Para obter mais informações sobre eventos, consulte [eventos](../../../visual-basic/programming-guide/language-features/events/index.md).  
  
> [!NOTE]
>  Código fora de uma classe, estrutura ou o módulo deve qualificar o nome de uma variável membro com o nome da classe, estrutura ou módulo. Código fora de que um procedimento ou bloco não pode se referir a todas as variáveis locais dentro desse procedimento ou bloco.  
  
## <a name="releasing-managed-resources"></a>Liberar recursos gerenciados  
 O coletor de lixo do .NET Framework libera os recursos gerenciados sem qualquer codificação extra de sua parte. No entanto, você pode forçar o descarte de um recurso gerenciado em vez de esperar o coletor de lixo.  
  
 Se uma classe mantiver um recurso particularmente importante e escasso (como um identificador de arquivo ou a conexão de banco de dados), não convém esperar até a próxima coleta de lixo para limpar uma instância da classe que não está mais em uso. Uma classe pode implementar o <xref:System.IDisposable> interface para fornecer uma maneira para liberar recursos antes de uma coleta de lixo. Uma classe que implementa essa interface expõe um `Dispose` método que pode ser chamado para forçar valiosos recursos sejam liberados imediatamente.  
  
 O `Using` instrução automatiza o processo de aquisição de um recurso, executando um conjunto de instruções e, em seguida, descarte do recurso. No entanto, o recurso deve implementar o <xref:System.IDisposable> interface. Para obter mais informações, consulte [Instrução using](../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir declara variáveis usando a `Dim` instrução com várias opções.  
  
 [!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir lista os números primos entre 1 e 30. O escopo de variáveis locais é descrito nos comentários de código.  
  
 [!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o `speedValue` variável é declarada no nível de classe. O `Private` palavra-chave é usada para declarar a variável. A variável pode ser acessada por qualquer procedimento de `Car` classe.  
  
 [!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]  
  
 [!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Instrução Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)  
 [Declaração de Variável](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Inicializadores de objeto: tipos nomeados e anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Como declarar um objeto usando um inicializador de objeto](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
