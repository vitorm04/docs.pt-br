---
title: "Refer&#234;ncias e a instru&#231;&#227;o Imports (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "assemblies [Visual Basic], namespaces"
  - "assemblies [Visual Basic], referências"
  - "Instrução Imports, referenciando assemblies"
  - "namespaces, assemblies"
  - "referências, assembly"
  - "referenciando assemblies"
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Refer&#234;ncias e a instru&#231;&#227;o Imports (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Você pode tornar externos objetos disponíveis para o projeto escolhendo o comando  **Adicionar Referência**  no menu **Projeto**.  Referências em [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] podem apontar para conjuntos de módulos \(assemblies\), que são como bibliotecas mas contêm mais informações.  
  
## A declaração Imports  
 Conjuntos de Módulos \(Assemblies\) incluem um ou mais NameSpaces.  Quando você adiciona uma referência a um conjunto de módulos \(assembly\), você também pode adicionar uma  instrução `Imports` em um módulo que controla a visibilidade dos namespaces daquele assembly dentro do módulo.  A instrução `Imports` fornece um contexto de escopo que permite que você use apenas a parte do namespace necessária para fornecer uma referência única.  
  
 A instrução `Imports` possui a seguinte sintaxe:  
  
 `Imports` \[         `|` `Aliasname` \=\] `Namespace`  
  
 `Aliasname`refere\-se para um nome curto, que você pode usar para se referir a um namespace importado dentro do código.  `Namespace`é uma referência de projeto, por meio de uma definição de dentro do projeto ou um anterior de um espaço para nome disponível por meio de um `Imports` instrução.  
  
 Um módulo pode conter qualquer número de instruções `Imports` .  Elas devem aparecer após quaisquer instruções `Option`, se alguma estiver presente, mas antes de qualquer outro código.  
  
> [!NOTE]
>  Não confunda referências de projeto com a instrução `Imports` ou a instrução `Declare`.  Referências de projeto tornam objetos externos, como objetos de conjuntos de módulos \(assemblies\), disponíveis para  projetos [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  A instrução `Imports` é usada para simplificar o acesso às referências de projeto, mas não fornece acesso a esses objetos.  A instrução `Declare` é usada para declarar uma referência a um procedimento externo em uma biblioteca de vínculo dinâmico \(DLL\).  
  
## Usando aliases com a instrução Imports  
 A instrução `Imports` facilita o acesso a métodos de classes, eliminando a necessidade para digitar explicitamente os nomes totalmente qualificados das referências.  Os aliases permitem que você atribua um nome amigável a apenas uma parte de um namespace.  Por exemplo, a sequência retorno de carro\/linha alimentação que faz com que um único seguimento de texto seja exibido em várias linhas é parte do módulo <xref:Microsoft.VisualBasic.ControlChars> no namespace <xref:Microsoft.VisualBasic?displayProperty=fullName>.  Para usar essa constante em um programa sem um alias, você precisará digitar o seguinte código:  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 As instruções `Imports` devem sempre ser as primeiras linhas imediatamente após quaisquer instruções `Option` em um módulo.  O fragmento de código a seguir mostra como importar e atribuir um alias ao módulo <xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>:  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 Referências futuras a esse namespace podem ser consideravelmente menores:  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 Se uma instrução `Imports` não incluir um nome de alias, elementos definidos no namespace importado podem ser usados no módulo sem qualificação.  Se o nome do alias for especificado, ele deve ser usado como um qualificador para os nomes contidos naquele namespace.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic>   
 [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/pt-br/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Namespaces no Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Assemblies e o cache de assemblies global](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [Como criar e usar assemblies usando a linha de comando](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instrução Imports \(tipo e namespace .NET\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)