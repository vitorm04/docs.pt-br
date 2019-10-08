---
title: Lista de atributos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: 771757afe214919649e13fda3990e1154be8e1e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004533"
---
# <a name="attribute-list-visual-basic"></a>Lista de atributos (Visual Basic)
Especifica os atributos a serem aplicados a um elemento de programação declarado. Vários atributos são separados por vírgulas. Veja a seguir a sintaxe de um atributo.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a>Partes  
|||
|---|---|
|`attributemodifier`|Necessário para atributos aplicados no início de um arquivo de origem. Pode ser [assembly](../../../visual-basic/language-reference/modifiers/assembly.md) ou [módulo](../../../visual-basic/language-reference/modifiers/module-keyword.md).|
|`attributename`| Necessário. Nome do atributo.|
|`attributearguments`|Opcional. Lista de argumentos posicionais para este atributo. Vários argumentos são separados por vírgulas.|
|`attributeinitializer`|Opcional. Lista de inicializadores de variável ou propriedade para este atributo. Vários inicializadores são separados por vírgulas.|
  
## <a name="remarks"></a>Comentários  
 Você pode aplicar um ou mais atributos a praticamente qualquer elemento de programação (tipos, procedimentos, propriedades e assim por diante). Os atributos aparecem nos metadados do assembly e podem ajudá-lo a anotar seu código ou especificar como usar um elemento de programação específico. Você pode aplicar atributos definidos por Visual Basic e o .NET Framework, e pode definir seus próprios atributos.  

 Para obter mais informações sobre quando usar atributos, consulte [visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md). Para obter informações sobre nomes de atributo, consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Regras  
  
- **Placement.** Você pode aplicar atributos aos elementos de programação mais declarados. Para aplicar um ou mais atributos, você coloca um *bloco de atributo* no início da declaração do elemento. Cada entrada na lista de atributos especifica um atributo que você deseja aplicar e o modificador e os argumentos que você está usando para essa invocação do atributo.  
  
- **Colchetes angulares.** Se você fornecer uma lista de atributos, deverá colocá-la entre colchetes angulares ("`<`" e "`>`").  
  
- **Parte da declaração.** O atributo deve ser parte da declaração do elemento, não de uma instrução separada. Você pode usar a sequência de continuação de linha ("`_`") para estender a instrução de declaração em várias linhas de código-fonte.  
  
- **Modificadores.** Um modificador de atributo (`Assembly` ou `Module`) é necessário em todos os atributos aplicados a um elemento de programação no início de um arquivo de origem. Modificadores de atributo não são permitidos em atributos aplicados a elementos que não estão no início de um arquivo de origem.  
  
- **Argumentos.** Todos os argumentos posicionais de um atributo devem preceder qualquer inicializador de variável ou propriedade.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir aplica o atributo <xref:System.Runtime.InteropServices.DllImportAttribute> a uma definição de esqueleto de um procedimento `Function`.  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <xref:System.Runtime.InteropServices.DllImportAttribute> indica que o procedimento atribuído representa um ponto de entrada em uma biblioteca de vínculo dinâmico (DLL) não gerenciada. O atributo fornece o nome da DLL como um argumento posicional e as outras informações como inicializadores de variável.  
  
## <a name="see-also"></a>Consulte também

- [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md)
- [Módulo \<palavra-chave >](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [Visão geral de atributos](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Como: quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
