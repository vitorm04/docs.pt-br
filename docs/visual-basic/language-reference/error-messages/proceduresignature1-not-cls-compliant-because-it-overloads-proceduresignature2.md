---
title: <proceduresignature1> não está em conformidade com CLS porque sobrecarrega <proceduresignature2> que difere dele somente pelos tipos de matriz e parâmetro de matriz ou pela classificação dos tipos de parâmetro da matriz
ms.date: 07/20/2015
f1_keywords:
- vbc40035
- bc40035
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
ms.openlocfilehash: 6143ebfbe7f131b0e196e531ed4282c8333be4ea
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250178"
---
# <a name="proceduresignature1-is-not-cls-compliant-because-it-overloads-proceduresignature2-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a>\<proceduresignature1 > não tem conformidade com CLS porque sobrecarrega @no__t > que difere dele apenas por matriz de tipos de parâmetro de matriz ou pela classificação dos tipos de parâmetro de matriz

Um procedimento ou propriedade é marcado como `<CLSCompliant(True)>` quando ele substitui outro procedimento ou propriedade e a única diferença entre suas listas de parâmetros é o nível de aninhamento de uma matriz denteada ou a classificação de uma matriz.
  
 Nas declarações a seguir, a segunda e terceira declarações geram esse erro:
  
 `Overloads Sub ProcessArray(arrayParam() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam()() As Integer)`  
  
 `Overloads Sub ProcessArray(arrayParam(,) As Integer)`  
  
 A segunda declaração altera o parâmetro unidimensional original `arrayParam` para uma matriz de matrizes. A terceira declaração altera `arrayParam` para uma matriz bidimensional (Rank 2). Embora Visual Basic permita sobrecargas para diferir apenas por uma dessas alterações, esse sobrecarregamento não é compatível com a [independência de linguagem e com os componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS).  
  
 Ao aplicar o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo como `True` ou `False` para indicar a conformidade ou a não conformidade. Não há nenhum padrão para esse parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele será considerado não compatível.  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC40035  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se você precisar de conformidade com CLS, defina suas sobrecargas para diferir umas das outras em mais formas do que apenas as alterações citadas nesta página de ajuda.
- Se você precisar que as sobrecargas diferem apenas pelas alterações citadas nesta página de ajuda, remova o <xref:System.CLSCompliantAttribute> de suas definições ou marque-os como `<CLSCompliant(False)>`.
  
## <a name="see-also"></a>Consulte também

- [Sobrecarga de Procedimento](../../programming-guide/language-features/procedures/procedure-overloading.md)
- [Sobrecargas](../modifiers/overloads.md)
