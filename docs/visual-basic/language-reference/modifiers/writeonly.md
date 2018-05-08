---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Especifica que uma propriedade pode ser gravada mas não lida.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
 **Contexto de declaração.** Você pode usar `WriteOnly` apenas no nível de módulo. Isso significa que o contexto da declaração para um `WriteOnly` propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
 Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.  
  
## <a name="when-to-use-writeonly"></a>Quando usar WriteOnly  
 Às vezes você deseja ser capaz de definir um valor, mas não descobrir o que é o código. Por exemplo, dados confidenciais, como um número de registro social ou uma senha, precisam ser protegidos contra o acesso por qualquer componente que não definido. Nesses casos, você pode usar um `WriteOnly` propriedade para definir o valor.  
  
> [!IMPORTANT]
>  Quando você definir e usar um `WriteOnly` propriedade, considere as seguintes medidas de proteção adicionais:  
  
-   **Substituindo.** Se a propriedade for um membro de uma classe, permitir que ele seja padrão [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não o declare `Overridable` ou `MustOverride`. Isso impede que uma classe derivada faça um acesso indesejado através de uma substituição.  
  
-   **Nível de acesso.** Se você mantiver dados confidenciais a propriedade em uma ou mais variáveis, declare-los [privada](../../../visual-basic/language-reference/modifiers/private.md) para que nenhum outro código possa acessá-los.  
  
-   **Criptografia.** Armazene todos os dados confidenciais em formato criptografado em vez de em texto sem formatação. Se alguma forma, o código mal-intencionado obtiver acesso a área da memória, é mais difícil fazer uso dos dados. A criptografia também é útil se for necessário serializar os dados confidenciais.  
  
-   **A redefinição.** Quando a classe, estrutura ou módulo definindo a propriedade está sendo finalizado, redefina os dados confidenciais para valores padrão ou outros valores sem sentido. Isso proporciona proteção extra quando essa área da memória é liberada para acesso geral.  
  
-   **Persistência.** Não mantenha quaisquer dados confidenciais, por exemplo, no disco, se for possível evitar. Além disso, não grave dados confidenciais na área de transferência.  
  
 O `WriteOnly` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
