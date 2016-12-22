---
title: "Enumera&#231;&#245;es e qualifica&#231;&#227;o de nome (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nomes ambíguos, enumerações"
  - "declarações, enumerações"
  - "declarações, namespaces"
  - "declarando enumerações"
  - "declarando namespaces, enumerações"
  - "enumerações [Visual Basic], qualificação de nome"
  - "Instrução Imports, declarações de namespace"
  - "conflitos de nome"
  - "nomes, evitando conflitos"
  - "namespaces, declarando"
  - "conflitos de nomes, enumerações"
  - "conflitos de nomes, qualificando nomes"
  - "convenções de nomenclatura, conflitos de nomes"
  - "referências, membros de enumeração"
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Enumera&#231;&#245;es e qualifica&#231;&#227;o de nome (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Normalmente, ao se referir a um membro de uma enumeração, você deve qualificar o nome do membro com o nome de enumeração.  Por exemplo, para se referir ao membro `Sunday` de sua enumeração `Days`, você usaria a sintaxe a seguir:  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## Usando a instrução Imports  
 Você pode evitar o uso de nomes totalmente qualificados, adicionando uma instrução `Imports` à seção de declarações de namespaces do seu código, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 Uma instrução `Imports` importa nomes de namespaces de projetos referenciados e conjuntos de módulos \(assemblies\) e do mesmo projeto como o módulo no qual a instrução aparece.  Depois que essa instrução é adicionada, você pode consultar os membros da enumeração sem qualificação, como no exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 Organizando conjuntos de constantes relacionadas em enumerações, você pode usar os mesmos nomes de constantes em contextos diferentes.  Por exemplo, você pode usar os mesmos nomes para as constantes dias da semana nas enumerações `Days` e `WorkDays`.  Se você usar a instrução `Imports` com suas enumerações, você deve ter cuidado para evitar referências ambíguas.  Considere o exemplo a seguir:  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 Supondo\-se que `Monday` seja um membro da enumeração `Days` e da enumeração `Workdays`, esse código gerará um erro do compilador.  Para evitar referências ambíguas quando se referir a uma constante individual, qualificar o nome constante com sua enumeração.  O código a seguir se refere à constante `Saturday` nas enumerações `Days` e `WorkDays`.  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## Consulte também  
 [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Como declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Como fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Como iterar em uma enumeração no Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [Como determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Tipos de dados constante e literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Instrução Imports \(tipo e namespace .NET\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Tipos de dados](../../../../visual-basic/language-reference/data-types/data-type-summary.md)