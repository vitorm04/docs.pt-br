---
title: "Instru&#231;&#227;o Const (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "instrução Const [Visual Basic]"
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o Const (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Declara e define uma ou mais constantes.  
  
## Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## Partes  
 `attributelist`  
 Opcional.  Lista de atributos que se aplicam a todas as constantes declaradas nessa declaração.  Consulte [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes \("`<`" e "`>`"\).  
  
 `accessmodifier`  
 Opcional.  Use isso para especificar qual código pode acessar essas constantes.  Pode ser [Público](../../../visual-basic/language-reference/modifiers/public.md), [Protegido](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, ou [Particular](../../../visual-basic/language-reference/modifiers/private.md).  
  
 `Shadows`  
 Opcional.  Use isto para redeclarar e ocultar um elemento de programação numa classe base.  Acesse [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Obrigatório.  Lista de constantes que está sendo declarada nessa declaração.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Cada `constant` possui a seguinte sintaxe e partes:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Parte|Descrição|  
|-----------|---------------|  
|`constantname`|Obrigatório.  Nome da constante.  Consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Necessário se `Option Strict` estiver `On`.  Tipo de dados da constante.|  
|`initializer`|Obrigatório.  Expressão que é avaliada em tempo de compilação e atribuída à constante.|  
  
## Comentários  
 Se você tiver um valor que nunca é alterado em seu aplicativo, você pode definir uma constante nomeada e usá\-la no lugar de um valor literal.  Um nome é mais fácil de lembrar que um valor.  Você pode definir a constante apenas uma vez e usá\-la em vários locais no seu código.  Se em uma versão posterior você precisar redefinir o valor, a declaração `Const` é o único local em que você precisará fazer uma alteração.  
  
 Você pode usar `Const` somente no nível de módulo ou procedimento.  Isso significa que o *contexto da declaração*  para uma variável deve ser uma classe, estrutura, módulo, procedimento ou bloco, e não pode ser um arquivo fonte, namespace ou interface.  Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Constantes padrão locais \(dentro de um procedimento\) para acesso público e você não pode usar quaisquer modificadores de acesso nelas.  Constantes de classes e membros de módulo\(fora de qualquer procedimento\) padrão para acesso privado, e constantes de membro de estrutura padrão para acesso público.  Você pode ajustar os seus níveis de acesso com os modificadores de acesso.  
  
## Regras  
  
-   **Contexto da Declaração.** Uma constante declarado no nível de módulo, fora de qualquer procedimento, é um  *constante de membro*; ele é um membro da classe, estrutura ou módulo declara.  
  
     Uma constante declarada no nível de procedimento é uma  *constante local* ; ela é local para o procedimento ou bloco que a declara.  
  
-   **Atributos.** Você pode aplicar os atributos somente para constantes membro, não para constantes locais.  Um atributo contribui com informações para metadados do conjunto, que não é significativo para armazenamento temporário, como constantes locais.  
  
-   **Modificador.** Por padrão, todas as constantes são `Shared`, `Static`, e `ReadOnly`.  Não é possível usar qualquer uma dessas palavras\-chave ao declarar uma constante.  
  
     No nível de procedimento, você não pode usar `Shadows` ou qualquer modificador de acesso para declarar constantes locais.  
  
-   **Várias constantes.** Você pode declarar diversas constantes na mesma instrução de declaração, especificando a `constantname` parte para cada um deles.  Múltiplas constantes são separadas por vírgulas.  
  
## Regras de Tipo de Dados  
  
-   **Tipos de dados.** O `Const` instrução pode declarar o tipo de dados de uma variável.  Você pode especificar qualquer tipo de dados ou o nome de uma enumeração.  
  
-   **Tipo Padrão.** Se você não especificar `datatype`, a constante leva o tipo de dados de `initializer`.  Se você especificar `datatype` e `initializer`, o tipo de dados do `initializer` deve ser conversível para `datatype`.  Se nem `datatype` ou `initializer` estiverem presentes, o tipo de dados padrão será `Object`.  
  
-   **Tipos diferentes.** Você pode especificar os tipos de dados diferentes para diferentes constantes usando um separado `As` cláusula para cada variável declarada.  No entanto, você não pode declarar diversas constantes como do mesmo tipo, usando uma cláusula `As` comum.  
  
-   **Inicialização.** Você deve inicializar o valor de cada constante na `constantlist`.  Você usa `initializer` para fornecer uma expressão a ser atribuída à constante.  A expressão pode ser qualquer combinação de literais, outras constantes que já estão definidas, e membros de enumeração que já estão definidos.  Você pode usar operadores aritméticos e lógicos para combinar esses elementos.  
  
     Você não pode usar variáveis ou funções no `initializer`.  No entanto, você pode usar palavras\-chave de conversão, como `CByte` e `CShort`.  Você também pode usar `AscW` se você chamá\-lo com uma constante `String` ou argumento `Char`, desde que possa ser avaliado em tempo de compilação.  
  
## Comportamento  
  
-   **Escopo.** Constantes locais são acessíveis somente de dentro de seu procedimento ou bloco.  Constantes membro são acessíveis a partir em qualquer lugar dentro sua classe, estrutura ou módulo.  
  
-   **Qualificação** Código fora de uma classe, estrutura, ou o módulo deve qualificar um nome de constante membro com o nome dessa classe, estrutura ou módulo.  Código fora de um procedimento ou bloco não pode se referir a nenhuma constante local dentro desse procedimento ou bloco.  
  
## Exemplo  
 O exemplo a seguir utiliza a declaração `Const` para declarar constantes para uso no lugar de valores literais.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## Exemplo  
 Se você define uma constante com o tipo de dados `Object`, o compilador Visual Basic dá a ele o tipo de `initializer`, em vez de `Object`.  No exemplo a seguir, a constante `naturalLogBase` tem o tipo de tempo de execução `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 O exemplo anterior usa o método <xref:System.Type.ToString%2A> no objeto <xref:System.Type> retornado por [Operador GetType](../../../visual-basic/language-reference/operators/gettype-operator.md), porque <xref:System.Type> não pode ser convertida em `String` usando `CStr`.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Diretiva \#Const](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Conversões implícitas e explícitas](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Constantes e enumerações](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constantes e enumerações](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)