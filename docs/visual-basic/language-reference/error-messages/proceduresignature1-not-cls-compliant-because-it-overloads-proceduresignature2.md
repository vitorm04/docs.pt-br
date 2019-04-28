---
title: <proceduresignature1> não é compatível com CLS porque sobrecarrega <proceduresignature2> que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 0bda4ad6a4d5368d93e2ca603b78bf9db6aca858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920907"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > não é compatível com CLS porque sobrecarrega \<proceduresignature2 > que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz
Um procedimento ou propriedade é marcada como `<CLSCompliant(True)>` quando substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetros é o nível de aninhamento de uma matriz denteada ou a classificação de uma matriz.  
  
 Em declarações a seguir, as segunda e terceira declarações geram esse erro.  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes. A terceira declaração muda `arrayParam` para uma matriz bidimensional (posição 2). Enquanto o Visual Basic permite sobrecargas diferir somente por uma dessas alterações, essa sobrecarga não está em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Quando você aplica a <xref:System.CLSCompliantAttribute> a um elemento de programação, você definir o atributo `isCompliant` parâmetro a `True` ou `False` para indicar a compatibilidade ou incompatibilidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não se aplicam a <xref:System.CLSCompliantAttribute> a um elemento, ele é considerado incompatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40035  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se você precisar de conformidade com CLS, defina suas sobrecargas para diferem entre si em mais maneiras do que apenas as alterações citadas nessa página de Ajuda.  
  
- Se você precisar que as sobrecargas diferem somente por alterações citadas nesta ajuda da página, remova os <xref:System.CLSCompliantAttribute> de suas definições ou marcá-los como `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Consulte também

- [Sobrecarga de Procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)
