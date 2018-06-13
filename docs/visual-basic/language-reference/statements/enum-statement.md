---
title: Instrução Enum (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234010"
---
# <a name="enum-statement-visual-basic"></a>Instrução Enum (Visual Basic)
Declara uma enumeração e define os valores de seus membros.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a>Partes  
  
-   `attributelist`  
  
     Opcional. Lista de atributos que se aplicam a essa enumeração. Você deve colocar o [a lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares ("`<`"e"`>`").  
  
     O <xref:System.FlagsAttribute> atributo indica que o valor de uma instância de enumeração pode incluir vários membros de enumeração, e cada membro representa um campo de bit no valor de enumeração.  
  
-   `accessmodifier`  
  
     Opcional. Especifica o código pode acessar essa enumeração. Pode ser um dos seguintes:  
  
    -   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [Friend protegido](../../language-reference/modifiers/protected-friend.md)
    
    - [Privado protegido](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     Opcional. Especifica que esta enumeração redeclara e oculta um elemento de programação com o mesmo nome, ou um conjunto de elementos sobrecarregados, em uma classe base. Você pode especificar [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) somente na enumeração em si, não em qualquer um de seus membros.  
  
-   `enumerationname`  
  
     Necessário. Nome da enumeração. Para obter informações sobre nomes válidos, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Opcional. Tipo de dados de enumeração e todos os seus membros.  
  
-   `memberlist`  
  
     Necessário. Lista de constantes de membro que está sendo declarada nessa instrução. Vários membros aparecem em linhas de código de origem individuais.  
  
     Cada `member` tem a seguinte sintaxe e partes: `[<attribute list>] member name [ = initializer ]`  
  
    |Parte|Descrição|  
    |---|---|  
    |`membername`|Necessário. Nome desse membro.|  
    |`initializer`|Opcional. Expressão que é avaliada em tempo de compilação e atribuída a este membro.|  
  
-   `End` `Enum`  
  
     Encerra o `Enum` bloco.  
  
## <a name="remarks"></a>Comentários  
 Se você tiver um conjunto de valores sem variação que são logicamente relacionados uns aos outros, você pode defini-los juntos em uma enumeração. Isso fornece nomes significativos para a enumeração e seus membros, que são mais fáceis de lembrar que seus valores. Em seguida, você pode usar os membros de enumeração em vários locais no seu código.  
  
 Os benefícios de usar enumerações incluem o seguinte:  
  
-   Reduz os erros causados por Transpor ou números de erros de digitação.  
  
-   É fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, o que significa que é menos provável que serão introduzidos erros.  
  
-   Garante a compatibilidade com versões posteriores. Se você usar enumerações, seu código é menos provável falhe se futuramente alguém altera os valores correspondentes aos nomes de membros.  
  
 Uma enumeração tem um nome, um tipo de dados subjacente e um conjunto de membros. Cada membro representa uma constante.  
  
 Uma enumeração declarada na classe, estrutura, módulo ou nível de interface, fora de qualquer procedimento, é um *membro de enumeração*. É um membro de classe, estrutura, módulo ou interface que declara.  
  
 Enumerações de membro podem ser acessadas de qualquer lugar dentro de sua classe, estrutura, módulo ou interface. Código fora de uma classe, estrutura, ou módulo deve qualificar nome do membro de uma enumeração com o nome da classe, estrutura ou módulo. Você pode evitar a necessidade de usar nomes totalmente qualificados, adicionando uma [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrução para o arquivo de origem.  
  
 Uma enumeração declarada no nível de namespace, fora de qualquer classe, estrutura, módulo ou interface, é um membro do namespace no qual ele aparece.  
  
 O *contexto declaração* para uma enumeração deve ser um arquivo de origem, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Você pode aplicar atributos a uma enumeração como um todo, mas não a seus membros individualmente. Um atributo contribui com informações para metadados do assembly.  
  
## <a name="data-type"></a>Tipo de dados  
 O `Enum` instrução pode declarar o tipo de dados de uma enumeração. Cada membro tem o tipo de dados da enumeração. Você pode especificar `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort`.  
  
 Se você não especificar `datatype` para a enumeração, cada membro tem o tipo de dados do seu `initializer`. Se você especificar ambos `datatype` e `initializer`, o tipo de dados `initializer` deve ser conversível em `datatype`. Se nem `datatype` nem `initializer` estiver presente, o tipo de dados padrão é `Integer`.  
  
## <a name="initializing-members"></a>Membros de inicialização  
 O `Enum` instrução pode inicializar o conteúdo de membros selecionados na `memberlist`. Você usa `initializer` para fornecer uma expressão a ser atribuída ao membro.  
  
 Se você não especificar `initializer` para um membro, Visual Basic o inicializa com zero (se ele for o primeiro `member` na `memberlist`), ou para um valor maior do que o precede imediatamente `member`.  
  
 A expressão fornecida em cada `initializer` pode ser qualquer combinação de literais, outras constantes que já estão definidas e membros de enumeração que já estão definidos, incluindo um membro anterior dessa enumeração. Você pode usar operadores aritméticos e lógicos para combinar esses elementos.  
  
 Você não pode usar variáveis ou funções no `initializer`. No entanto, você pode usar palavras-chave de conversão, como `CByte` e `CShort`. Você também pode usar `AscW` se chamá-lo com uma constante `String` ou `Char` argumento, desde que possa ser avaliado em tempo de compilação.  
  
 Enumerações não podem ter valores de ponto flutuante. Se um membro é atribuído um valor de ponto flutuante e `Option Strict` é definida como on, ocorre um erro do compilador. Se `Option Strict` estiver desativado, o valor é convertido automaticamente para o `Enum` tipo.  
  
 Se o valor de um membro exceder o intervalo permitido para o tipo de dados, ou se você inicializar qualquer membro para o valor máximo permitido pelo tipo de dados subjacente, o compilador relata um erro.  
  
## <a name="modifiers"></a>Modificadores  
 Classe, estrutura, módulo e padrão de enumerações de membro de interface de acesso público. Você pode ajustar os níveis de acesso com os modificadores de acesso. Padrão de enumerações de membro de Namespace para acesso friend. Você pode ajustar os níveis de acesso para público, mas não a particular ou protegido. Para obter mais informações, consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Todos os membros de enumeração têm acesso público e você não pode usar quaisquer modificadores de acesso neles. No entanto, se a enumeração tiver um nível de acesso mais restrito, o nível de acesso especificado enumeração tem precedência.  
  
 Por padrão, todas as enumerações são tipos e seus campos são constantes. Portanto, o `Shared`, `Static`, e `ReadOnly` palavras-chave não podem ser usadas ao declarar uma enumeração ou seus membros.  
  
## <a name="assigning-multiple-values"></a>Atribuindo valores múltiplos  
 Enumerações geralmente representam valores mutuamente exclusivos. Incluindo o <xref:System.FlagsAttribute> atributo o `Enum` declaração, você pode em vez disso, atribuir vários valores para uma instância da enumeração. O <xref:System.FlagsAttribute> atributo especifica que a enumeração ser tratado como um campo de bits, ou seja, um conjunto de sinalizadores. Esses são chamados de *bit a bit* enumerações.  
  
 Quando você declara uma enumeração usando o <xref:System.FlagsAttribute> atributo, é recomendável que você use potências de 2, que é 1, 2, 4, 8, 16 e assim por diante, para os valores. Também recomendamos que "None" seja o nome de um membro cujo valor é 0. Para obter diretrizes adicionais, consulte <xref:System.FlagsAttribute> e <xref:System.Enum>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `Enum` instrução. Observe que o membro é conhecido como `EggSizeEnum.Medium`e não como `Medium`.  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O método no exemplo a seguir está fora do `Egg` classe. Portanto, `EggSizeEnum` é totalmente qualificado como `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Enum` chamada de instrução para definir um conjunto relacionado de valores constantes. Nesse caso, os valores são cores, que você pode escolher para criar formulários de entrada de dados para um banco de dados.  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os valores que incluem números positivos e negativos.  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma `As` cláusula é usada para especificar o `datatype` de uma enumeração.  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar uma enumeração de bit a bit. Vários valores podem ser atribuídos a uma instância de uma enumeração de bit a bit. O `Enum` declaração inclui o <xref:System.FlagsAttribute> atributo, que indica que a enumeração pode ser tratada como um conjunto de sinalizadores.  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir itera por meio de uma enumeração. Ele usa o <xref:System.Enum.GetNames%2A> método para recuperar uma matriz de nomes de membro de enumeração, e <xref:System.Enum.GetValues%2A> para recuperar uma matriz de valores de membro.  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Conversões Implícitas e Explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Constantes e Enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)
