---
title: "&lt;proceduresignature1&gt; n&#227;o &#233; compat&#237;vel com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele somente pelos tipos de matriz e par&#226;metro de matriz ou pela classifica&#231;&#227;o dos tipos de par&#226;metro da matriz | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40035"
  - "bc40035"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40035"
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;proceduresignature1&gt; n&#227;o &#233; compat&#237;vel com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele somente pelos tipos de matriz e par&#226;metro de matriz ou pela classifica&#231;&#227;o dos tipos de par&#226;metro da matriz
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um procedimento ou propriedade é marcada como `<CLSCompliant(True)>` quando substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetro é o nível de aninhamento de um array denteado ou a posição de um array.  
  
 Nas declarações a seguir, as segunda e terceira declarações geram esse erro.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 A segunda declaração altera o parâmetro unidimensional original `arrayParam` para um array de arrays.  A terceira declaração muda `arrayParam` para um array bidimensional \(tamanho 2\).  Enquanto o Visual Basic permite sobrecargas para diferir somente por uma dessas alterações, tais sobrecargas não são compatíveis com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40035  
  
### Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina suas sobrecargas para diferirem umas das outras em mais maneiras do que somente as alterações citadas nessa página de Ajuda.  
  
-   Se você precisar que as sobrecargas sejam diferentes somente pelas alterações citadas nessa página da Ajuda, remova os <xref:System.CLSCompliantAttribute> de suas definições ou marque\-os como `<CLSCompliant(False)>`.  
  
## Consulte também  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)