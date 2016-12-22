---
title: "Parcial (Visual Basic) | Microsoft Docs"
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
  - "vb.Partial"
  - "partial"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic]"
  - "classes [Visual Basic], parcial"
  - "palavra-chave Partial [Visual Basic]"
  - "parcial, classes [Visual Basic]"
  - "parcial, estruturas"
  - "parcial, tipos [Visual Basic]"
  - "estruturas, parcial"
  - "promoção de tipo"
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
caps.latest.revision: 36
caps.handback.revision: 36
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Parcial (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indica que uma declaração de tipo é uma definição parcial do tipo.  
  
 Você pode dividir a definição de um tipo entre várias declarações usando o `Partial` palavra\-chave.  Você pode usar quantas declarações parciais conforme desejado, em quantos arquivos de origem diferentes conforme desejado.  No entanto, todas as declarações devem estar no mesmo assembly e o mesmo namespace.  
  
> [!NOTE]
>  Visual Basic oferece suporte *métodos parciais*, que são normalmente implementados em classes parciais.  Para obter mais informações, consulte [Métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md) e [Instrução Sub](../../../visual-basic/language-reference/statements/sub-statement.md).  
  
## Sintaxe  
  
```  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`attrlist`|Opcional.  Lista de atributos que se aplicam a esse tipo.  Você deve colocar o [Lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md) entre colchetes angulares \(`< >`\).|  
|`accessmodifier`|Opcional.  Especifica qual código pode acessar esse tipo.  Consulte [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Opcional.  Consulte [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Opcional.  Consulte [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Opcional.  Consulte [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`name`|Obrigatório.  Nome deste tipo.  Deve corresponder ao nome definido em todas as outras declarações parciais do mesmo tipo.|  
|`Of`|Opcional.  Especifica que este é um tipo genérico.  Consulte [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|Necessário se você usar [de](../../../visual-basic/language-reference/statements/of-clause.md).  Consulte [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Opcional.  Consulte [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Necessário se você usar `Inherits`.  O nome da classe ou da interface da qual essa classe deriva.|  
|`Implements`|Opcional.  Consulte [Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Necessário se você usar `Implements`.  Os nomes das interfaces que esse tipo implementa.|  
|`variabledeclarations`|Opcional.  Instruções que declaram variáveis adicionais e eventos para o tipo.|  
|`proceduredeclarations`|Opcional.  Instruções que declaram e definem procedimentos adicionais para o tipo.|  
|`End Class` ou `End Structure`|Termina a essa parcial `Class` ou `Structure` definição.|  
  
## Comentários  
 Visual Basic usa definições de classe parcial para separar o código gerado de usuário\-autoria código em arquivos de origem separado.  Por exemplo, o **Windows Form Designer** define classes parciais para controles, como <xref:System.Windows.Forms.Form>.  Você não deve modificar o código gerado nesses controles.  
  
 Todas as regras para a classe, estrutura, interface e criação de módulo, como aquelas para uso de modificador e herança, se aplicam ao criar um tipo parcial.  
  
## Práticas recomendadas  
  
-   Em circunstâncias normais, você não deve dividir o desenvolvimento de um único tipo entre dois ou mais declarações.  Portanto, na maioria dos casos não é necessário o `Partial` palavra\-chave.  
  
-   Para facilitar a leitura, cada declaração parcial de um tipo deve incluir o `Partial` palavra\-chave.  O compilador permite no máximo uma declaração parcial omitir a palavra\-chave; Se dois ou mais omiti\-lo o compilador sinaliza um erro.  
  
## Comportamento  
  
-   **União de declaração.** O compilador trata o tipo como a união de todas as suas declarações parciais.  Cada modificador de cada definição parcial aplica\-se ao tipo de inteiro e todos os membros de cada definição parcial estão disponível para o tipo inteiro.  
  
-   **Promoção de tipo não permitida para tipos parciais em módulos.** Se for uma definição parcial dentro de um módulo, promoção de tipos desse tipo será automaticamente derrotada.  Nesse caso, um conjunto de definições parciais pode causar resultados inesperados e até mesmo erros de compilador.  Para obter mais informações, consulte [Promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
     O compilador mescla definições parciais somente quando seus caminhos totalmente qualificados são idênticos.  
  
 O `Partial` palavra\-chave pode ser usada nesses contextos:  
  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
## Exemplo  
 O exemplo a seguir divide a definição de classe `sampleClass` em duas declarações, cada um deles define outro `Sub` procedimento.  
  
 [!code-vb[VbVbalrKeywords#3](../../../visual-basic/language-reference/codesnippet/VisualBasic/partial_1.vb)]  
  
 As duas definições parciais no exemplo anterior pode ser no mesmo arquivo de origem ou em dois arquivos de origem diferentes.  
  
## Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Promoção de tipos](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)   
 [Sombras](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)