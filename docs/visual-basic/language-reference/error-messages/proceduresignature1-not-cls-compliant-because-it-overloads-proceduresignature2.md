---
title: '&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz'
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0d150dad8d32b4bfa2b9e549e068ef24382d0eba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>&lt;proceduresignature1&gt; não é compatível com CLS porque sobrecarrega &lt;proceduresignature2&gt; que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz
Um procedimento ou propriedade é marcada como `<CLSCompliant(True)>` quando substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetro é o nível de aninhamento de uma matriz denteada ou a posição de uma matriz.  
  
 Em declarações a seguir, as segunda e terceira declarações geram esse erro.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes. A terceira declaração muda `arrayParam` para uma matriz bidimensional (posição 2). Enquanto o Visual Basic permite sobrecargas diferir somente por uma dessas alterações, tais sobrecargas não são compatíveis com o [independência da linguagem e componentes independentes da linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> para um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40035  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você precisar de compatibilidade com CLS, defina suas sobrecargas para diferem entre si em mais maneiras do que apenas as alterações citadas nessa página de Ajuda.  
  
-   Se você precisar que as sobrecargas sejam diferentes somente pelas alterações citadas na Ajuda da página, remova o <xref:System.CLSCompliantAttribute> de suas definições ou marcá-los como `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Consulte também  
   
 [Sobrecarga de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)  
 [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
