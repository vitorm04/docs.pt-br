---
title: "Instrução Enum (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Enum
dev_langs:
- VB
helpviewer_keywords:
- enumerated constants
- Enum statement
- Private keyword, Enum statements
- Public keyword, in Enum statement
- variables [Visual Basic], enumeration
- constants, enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: 44
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f9d3377300d30fd045c041367a528766fa9a8ed9
ms.lasthandoff: 03/13/2017

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
  
     O <xref:System.FlagsAttribute>atributo indica que o valor de uma instância de enumeração pode incluir vários membros de enumeração, e cada membro representa um campo de bit no valor de enumeração.</xref:System.FlagsAttribute>  
  
-   `accessmodifier`  
  
     Opcional. Especifica qual código pode acessar essa enumeração. Pode ser uma das seguintes opções:  
  
    -   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
     Você pode especificar `Protected``Friend` para permitir o acesso do código dentro classe de enumeração da, uma classe derivada ou o mesmo assembly.  
  
-   `Shadows`  
  
     Opcional. Especifica que enumeração redeclara e oculta um elemento de programação de nome idêntico, ou conjunto de elementos sobrecarregados, na classe base. Você pode especificar [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) somente na enumeração em si, não em qualquer um dos seus membros.  
  
-   `enumerationname`  
  
     Necessário. Nome da enumeração. Para obter informações sobre nomes válidos, consulte [nomes de elemento declarado](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `datatype`  
  
     Opcional. Tipo de dados de enumeração e todos os seus membros.  
  
-   `memberlist`  
  
     Necessário. Lista de constantes de membro sendo declarada nessa instrução. Vários membros aparecem em linhas de código fonte individual.  
  
     Cada `member` tem a seguinte sintaxe e partes:`[<attribute list>] member name [ = initializer ]`  
  
    |Parte|Descrição|  
    |---|---|  
    |`membername`|Necessário. Nome desse membro.|  
    |`initializer`|Opcional. Expressão que é avaliada em tempo de compilação e atribuída a esse membro.|  
  
-   `End` `Enum`  
  
     Encerra o `Enum` bloco.  
  
## <a name="remarks"></a>Comentários  
 Se você tiver um conjunto de valores sem variação que são logicamente relacionados uns aos outros, você pode defini-los juntos em uma enumeração. Isso fornece nomes significativos para a enumeração e seus membros, que são mais fáceis de lembrar que seus valores. Em seguida, você pode usar os membros de enumeração em muitos lugares no seu código.  
  
 Os benefícios de usar enumerações incluem o seguinte:  
  
-   Reduz erros causados por transpondo ou números de erros de digitação.  
  
-   É fácil alterar os valores no futuro.  
  
-   Torna o código mais fácil de ler, que significa que é menos provável que os erros serão lançados.  
  
-   Garante a compatibilidade com versões posteriores. Se você usar enumerações, seu código é menor probabilidade de falhar se futuramente alguém altera os valores correspondentes aos nomes de membro.  
  
 Uma enumeração tem um nome, um tipo de dados subjacente e um conjunto de membros. Cada membro representa uma constante.  
  
 Uma enumeração declarada na classe, estrutura, módulo ou nível de interface, fora de qualquer procedimento, é um *membro de enumeração*. Ele é um membro de classe, estrutura, módulo ou interface que o declara.  
  
 Enumerações de membro podem ser acessadas de qualquer lugar dentro de sua classe, estrutura, módulo ou interface. Código fora de uma classe, estrutura, ou módulo deve qualificar nome do membro de uma enumeração com o nome da classe, estrutura ou módulo. Você pode evitar a necessidade de usar nomes totalmente qualificados, adicionando uma [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrução ao arquivo de origem.  
  
 Uma enumeração declarada no nível de namespace, fora de qualquer classe, estrutura, módulo ou interface, é um membro do namespace no qual ele aparece.  
  
 O *contexto declaração* para uma enumeração deve ser um arquivo fonte, namespace, classe, estrutura, módulo ou interface e não pode ser um procedimento. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Você pode aplicar atributos a uma enumeração como um todo, mas não a seus membros individualmente. Um atributo contribui com informações para metadados do assembly.  
  
## <a name="data-type"></a>Tipo de dados  
 O `Enum` instrução pode declarar o tipo de dados de uma enumeração. Cada membro tem o tipo de dados da enumeração. You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.  
  
 Se você não especificar `datatype` para a enumeração, cada membro tem o tipo de dados do seu `initializer`. Se você especificar ambas `datatype` e `initializer`, o tipo de dados `initializer` deve ser conversível para `datatype`. Se nem `datatype` nem `initializer` estiver presente, o tipo de dados padrão é `Integer`.  
  
## <a name="initializing-members"></a>Inicializando membros  
 O `Enum` instrução pode inicializar o conteúdo de membros selecionados na `memberlist`. Você usa `initializer` para fornecer uma expressão a ser atribuída ao membro.  
  
 Se você não especificar `initializer` para um membro, Visual Basic o inicializa com zero (se ele for o primeiro `member` na `memberlist`), ou para um valor maior do que o precede imediatamente `member`.  
  
 A expressão fornecida em cada `initializer` pode ser qualquer combinação de literais, outras constantes que já estão definidas e membros de enumeração que já estão definidos, incluindo um membro anterior dessa enumeração. Você pode usar operadores aritméticos e lógicos para combinar esses elementos.  
  
 Você não pode usar variáveis ou funções no `initializer`. No entanto, você pode usar palavras-chave de conversão como `CByte` e `CShort`. Você também pode usar `AscW` se você chamá-lo com uma constante `String` ou `Char` argumento, desde que possa ser avaliado em tempo de compilação.  
  
 Enumerações não podem ter valores de ponto flutuante. Se um membro é atribuído um valor de ponto flutuante e `Option Strict` é definida como on, ocorre um erro do compilador. Se `Option Strict` estiver desativado, o valor é convertido automaticamente para o `Enum` tipo.  
  
 Se o valor de um membro exceder o intervalo permitido para o tipo de dados, ou se você inicializar qualquer membro com o valor máximo permitido pelo tipo de dados subjacente, o compilador relata um erro.  
  
## <a name="modifiers"></a>Modificadores  
 Classe, estrutura, módulo e padrão de enumerações de membro de interface de acesso público. Você pode ajustar os níveis de acesso com os modificadores de acesso. Padrão de enumerações de membro de Namespace para acesso de amigo. Você pode ajustar os níveis de acesso para público, mas não a particular ou protegido. Para obter mais informações, consulte [níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Todos os membros de enumeração têm acesso público e você não pode usar quaisquer modificadores de acesso neles. No entanto, se a enumeração tiver um nível de acesso mais restrito, o nível de acesso especificado enumeração tem precedência.  
  
 Por padrão, todas as enumerações são tipos e seus campos são constantes. Portanto, o `Shared`, `Static`, e `ReadOnly` palavras-chave não podem ser usadas ao declarar uma enumeração ou seus membros.  
  
## <a name="assigning-multiple-values"></a>Atribuindo valores múltiplos  
 Enumerações geralmente representam valores mutuamente exclusivos. Incluindo o <xref:System.FlagsAttribute>atributo o `Enum` declaração, você pode em vez disso, atribuir vários valores para uma instância da enumeração.</xref:System.FlagsAttribute> O <xref:System.FlagsAttribute>atributo especifica que a enumeração ser tratado como um campo de bits, ou seja, um conjunto de sinalizadores.</xref:System.FlagsAttribute> Eles são chamados de *bit a bit* enumerações.  
  
 Quando você declara uma enumeração usando o <xref:System.FlagsAttribute>atributo, é recomendável que você use potência de 2, que é, 1, 2, 4, 8, 16 e assim por diante, para os valores.</xref:System.FlagsAttribute> Também recomendamos que "Nenhum" seja o nome de um membro cujo valor é 0. Para obter diretrizes adicionais, consulte <xref:System.FlagsAttribute>e <xref:System.Enum>.</xref:System.Enum> </xref:System.FlagsAttribute>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `Enum` instrução. Observe que o membro é conhecido como `EggSizeEnum.Medium`e não como `Medium`.  
  
 [!code-vb[41 VbEnumsTask](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 O método no exemplo a seguir está fora do `Egg` classe. Portanto, `EggSizeEnum` é totalmente qualificado como `Egg.EggSizeEnum`.  
  
 [!code-vb[VbEnumsTask&42;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Enum` instrução para definir um conjunto relacionado de valores constantes nomeados. Nesse caso, os valores são cores que você pode escolher para criar formulários de entrada de dados para um banco de dados.  
  
 [!code-vb[30 VbEnumsTask](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra os valores que incluem números positivos e negativos.  
  
 [!code-vb[VbEnumsTask&#31;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, uma `As` cláusula é usada para especificar o `datatype` de uma enumeração.  
  
 [!code-vb[VbEnumsTask n º&6;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar uma enumeração de bit a bit. Vários valores podem ser atribuídos a uma instância de uma enumeração de bit a bit. O `Enum` declaração inclui o <xref:System.FlagsAttribute>atributo, que indica que a enumeração pode ser tratada como um conjunto de sinalizadores.</xref:System.FlagsAttribute>  
  
 [!code-vb[VbEnumsTask&#61;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir itera por meio de uma enumeração. Ele usa o <xref:System.Enum.GetNames%2A>método para recuperar uma matriz de nomes de membro de enumeração, e <xref:System.Enum.GetValues%2A>para recuperar uma matriz de valores de membro.</xref:System.Enum.GetValues%2A> </xref:System.Enum.GetNames%2A>  
  
 [!code-vb[VbEnumsTask&#51;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Enum></xref:System.Enum>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Instrução Const](../../../visual-basic/language-reference/statements/const-statement.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Funções de conversão de tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Constantes e Enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)
