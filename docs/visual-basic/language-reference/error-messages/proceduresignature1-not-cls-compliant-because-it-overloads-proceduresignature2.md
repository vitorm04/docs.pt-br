---
title: "&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele somente na matriz dos tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 984c04a107444036b980439b231d27a8a81656c1
ms.lasthandoff: 03/13/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele somente na matriz dos tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz
Um procedimento ou propriedade é marcada como `<CLSCompliant(True)>` quando substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetro é o nível de aninhamento de um array denteado ou a posição de uma matriz.  
  
 Nas declarações a seguir, as segunda e terceira declarações geram esse erro.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes. A terceira declaração muda `arrayParam` para uma matriz bidimensional (tamanho 2). Enquanto o Visual Basic permite sobrecargas diferir somente por uma dessas alterações, tais sobrecargas não são compatíveis com o [independência da linguagem e componentes independentes de linguagem](https://msdn.microsoft.com/library/12a7a7h3) (CLS).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute>para um elemento de programação, você definir o atributo `isCompliant` parâmetro como `True` ou `False` para indicar compatibilidade ou incompatibilidade.</xref:System.CLSCompliantAttribute> Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute>a um elemento, ele é considerado incompatível.</xref:System.CLSCompliantAttribute>  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40035  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina suas sobrecargas para diferirem umas das outras em mais maneiras do que somente as alterações citadas nessa página da Ajuda.  
  
-   Se você precisar que as sobrecargas sejam diferentes somente pelas alterações citadas a Ajuda da página, remova a <xref:System.CLSCompliantAttribute>de suas definições ou marcá-los como `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute>  
  
## <a name="see-also"></a>Consulte também  
 [\<PAVE em > escrevendo código compatível com CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)   
 [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)   
 [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
