---
title: Instrução Const (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 9d2e0c7b2b81a79f95fa852b3975f4512d87f8e0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623989"
---
# <a name="const-statement-visual-basic"></a>Instrução Const (Visual Basic)
Declara e define uma ou mais constantes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Partes  
 `attributelist`  
 Opcional. Lista de atributos que se aplicam a todas as constantes declaradas nesta instrução. Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) colchetes angulares ("`<`"e"`>`").  
  
 `accessmodifier`  
 Opcional. Use isso para especificar qual código pode acessar essas constantes. Pode ser [pública](../../../visual-basic/language-reference/modifiers/public.md), [protegido](../../../visual-basic/language-reference/modifiers/protected.md), [amigo](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [privada](../../../visual-basic/language-reference/modifiers/private.md), ou [Private protegida](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 Opcional. Use isto para redeclarar e ocultar um elemento de programação em uma classe base. Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Necessário. Lista de constantes que está sendo declarado nesta instrução.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Cada `constant` tem a seguinte sintaxe e partes:  
  
 `constantname``[ As``datatype``] =``initializer`  
  
|Parte|Descrição|  
|----------|-----------------|  
|`constantname`|Necessário. Nome da constante. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Necessário se `Option Strict` é `On`. Tipo de dados da constante.|  
|`initializer`|Necessário. Expressão que é avaliada em tempo de compilação e atribuída à constante.|  
  
## <a name="remarks"></a>Comentários  
 Se você tiver um valor que nunca é alterado em seu aplicativo, você pode definir uma constante nomeada e usá-lo no lugar de um valor literal. Um nome é mais fácil lembrar-se de que um valor. Você pode definir a constante apenas uma vez e usá-lo em muitos lugares no seu código. Se em uma versão posterior, você precisará redefinir o valor, o `Const` instrução é o único local em que você precisa fazer uma alteração.  
  
 Você pode usar `Const` apenas no nível de módulo ou procedimento. Isso significa que o *contexto de declaração* para uma variável deve ser uma classe, estrutura, módulo, procedimento ou bloco e não pode ser um arquivo de origem, namespace ou interface. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Padrão de constantes locais (dentro de um procedimento) para acesso público e você não pode usar qualquer modificador de acesso sobre eles. Classe e módulo membro constantes (fora de qualquer procedimento) padrão para acesso privado e o padrão de constantes de membro de estrutura de acesso público. Você pode ajustar os níveis de acesso com os modificadores de acesso.  
  
## <a name="rules"></a>Regras  
  
- **Contexto da declaração.** Uma constante declarada no nível de módulo, fora de qualquer procedimento, é um *constante membro*; ele é um membro da classe, estrutura, ou módulo que o declara.  
  
     Uma constante declarada no nível de procedimento é um *constante local*; ela é local para o procedimento ou bloco em que o declara.  
  
- **Atributos.** Você pode aplicar atributos somente para constantes de membro, não para constantes locais. Um atributo contribui com informações para metadados do assembly, que não é significativo para armazenamento temporário, como constantes locais.  
  
- **Modificadores.** Por padrão, todas as constantes são `Shared`, `Static`, e `ReadOnly`. É possível usar qualquer uma dessas palavras-chave ao declarar uma constante.  
  
     No nível de procedimento, você não pode usar `Shadows` ou qualquer modificador de acesso para declarar constantes locais.  
  
- **Várias constantes.** Você pode declarar várias constantes na mesma instrução de declaração, especificando o `constantname` parte para cada uma delas. Várias constantes são separados por vírgulas.  
  
## <a name="data-type-rules"></a>Regras de tipo de dados  
  
- **Tipos de dados.** O `Const` instrução pode declarar o tipo de dados de uma variável. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração.  
  
- **Tipo de padrão.** Se você não especificar `datatype`, a constante tem o tipo de dados `initializer`. Se você especificar ambos `datatype` e `initializer`, o tipo de dados `initializer` deve ser conversível para `datatype`. Se nem `datatype` nem `initializer` estiver presente, o tipo de dados padrão é `Object`.  
  
- **Tipos diferentes.** Você pode especificar diferentes tipos de dados para constantes diferentes usando um separado `As` cláusula para cada variável declarada. No entanto, você não pode declarar várias constantes para ser do mesmo tipo usando um comum `As` cláusula.  
  
- **Inicialização.** Você deve inicializar o valor de cada constante na `constantlist`. Você usa `initializer` para fornecer uma expressão a ser atribuído à constante. A expressão pode ser qualquer combinação de literais, outras constantes que já estão definidos e membros de enumeração que já estão definidos. Você pode usar operadores aritméticos e lógicos para combinar esses elementos.  
  
     Você não pode usar variáveis ou funções no `initializer`. No entanto, você pode usar as palavras-chave de conversão, como `CByte` e `CShort`. Você também pode usar `AscW` se você chamá-lo com uma constante `String` ou `Char` argumento, desde que possa ser avaliado em tempo de compilação.  
  
## <a name="behavior"></a>Comportamento  
  
- **Escopo.** As constantes locais são acessíveis somente de dentro de seu procedimento ou bloco. Constantes de membro são acessíveis de qualquer lugar dentro da sua classe, estrutura ou módulo.  
  
- **Qualificação.** Código fora de uma classe, estrutura ou módulo deve qualificar o nome de uma constante membro com o nome da classe, estrutura ou módulo. Código fora de que um procedimento ou bloco não pode se referir a nenhuma constante local dentro desse procedimento ou bloco.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Const` instrução para declarar constantes para uso no lugar de valores literais.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Exemplo  
 Se você definir uma constante com o tipo de dados `Object`, o compilador do Visual Basic fornece a ele o tipo da `initializer`, em vez de `Object`. No exemplo a seguir, a constante `naturalLogBase` tem o tipo de tempo de execução `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 O exemplo anterior usa o <xref:System.Type.ToString%2A> método na <xref:System.Type> objeto retornado pela [operador GetType](../../../visual-basic/language-reference/operators/gettype-operator.md), pois <xref:System.Type> não pode ser convertido em `String` usando `CStr`.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Diretiva #Const](../../../visual-basic/language-reference/directives/const-directive.md)
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Constantes e Enumerações](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Constantes e Enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
