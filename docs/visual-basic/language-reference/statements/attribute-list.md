---
title: "Lista de atributos (Visual Basic) | Microsoft Docs"
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
  - "lista de atributos"
  - "atributos [Visual Basic], aplicando"
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lista de atributos (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica os atributos a serem aplicados a um elemento de programação declarado.  Diversos parâmetros são separados por vírgulas.  A seguir está a sintaxe para um atributo.  
  
## Sintaxe  
  
```  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## Partes  
 `attributemodifier`  
 Necessário para os atributos aplicados no início de uma arquivo fonte.  Pode ser [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [Módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md).  
  
 `attributename`  
 Obrigatório.  Nome do atributo.  
  
 `attributearguments`  
 Opcional.  Lista de argumentos posicionais para este atributo.  Múltiplos argumentos são separados por vírgulas.  
  
 `attributeinitializer`  
 Opcional.  Lista de variáveis ou propriedades inicializadoras para este atributo.  Inicializadores múltiplos são separados por vírgulas.  
  
## Comentários  
 Você pode aplicar um ou mais atributos para praticamente qualquer elemento de programação \(tipos, procedimentos, propriedades e etc\).  Atributos aparecem nos metadados do seu assembly, e eles podem ajudar você anotar o código ou especificar como deseja usar um determinado elemento de programação.  Você pode aplicar os atributos definidos pelo Visual Basic e Framework .NET, e você pode definir seus próprios atributos.  
  
 Para obter mais informações sobre quando usar os atributos, consulte [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md).  Para obter informações sobre nomes de atributo, consulte [Nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## Regras  
  
-   **Posicionamento.** Você pode aplicar atributos para a maioria dos elementos de programação declarados.  Para aplicar um ou mais atributos, você insere um  *bloco de atributo*  no início da declaração do elemento.  Cada entrada na lista de atributos especifica um atributo que deseja aplicar, e o modificador e argumentos que você está usando para esta chamada do atributo.  
  
-   **Colchetes.** Se você fornecer uma lista de atributos, deve colocar colchetes angulares \("`<`"e"`>`"\).  
  
-   **Parte da declaração.** O atributo deve ser parte da declaração do elemento, não uma instrução separada.  Você pode utilizar uma sequência de continuação de linha \(" `_`"\) para estender a instrução de declaração em várias linhas de código\-fonte.  
  
-   **Modificador.** Um modificador de atributo \(`Assembly` ou `Module`\) é necessária em todos os atributos aplicados a um elemento de programação no início de um arquivo de origem.  Modificadores de atributo não são permitidos em atributos aplicados aos elementos que não estão no início de um arquivo fonte.  
  
-   **Argumentos.** Todos os argumentos posicionais para um atributo devem preceder qualquer variável ou inicializadores de propriedade .  
  
## Exemplo  
 O exemplo seguinte aplica o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> à definição reduzida de um procedimento `Function`.  
  
 [!code-vb[VbVbalrStatements#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/attribute-list_1.vb)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indica que o procedimento atribuído representa um ponto de entrada em uma biblioteca Dynamic\-link não gerenciada \(DLL\).  O atributo fornece o nome da DLL como um argumento posicional e as outras informações como inicializadores de variável .  
  
## Consulte também  
 [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)   
 [Módulo \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Atributos](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como quebrar e combinar instruções no código](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)