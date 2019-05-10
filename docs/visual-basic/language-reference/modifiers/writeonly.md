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
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647671"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Especifica que uma propriedade pode ser gravada, mas não lido.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
 **Contexto da declaração.** Você pode usar `WriteOnly` apenas no nível de módulo. Isso significa que o contexto da declaração para um `WriteOnly` propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
 Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.  
  
## <a name="when-to-use-writeonly"></a>Quando usar WriteOnly  
 Às vezes você deseja ser capaz de definir um valor, mas descobre o que é o código de consumo. Por exemplo, dados confidenciais, como um CPF ou uma senha, precisam ser protegido contra o acesso por qualquer componente que não defini-lo. Nesses casos, você pode usar um `WriteOnly` propriedade para definir o valor.  
  
> [!IMPORTANT]
>  Quando você define e usa um `WriteOnly` propriedade, considere as seguintes medidas de proteção adicionais:  
  
- **Substituindo.** Se a propriedade for um membro de uma classe, permitir que ele seja o padrão [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não o declare `Overridable` ou `MustOverride`. Isso impede que uma classe derivada tornando o acesso indesejado por meio de uma substituição.  
  
- **Nível de acesso.** Se você mantiver dados confidenciais a propriedade em uma ou mais variáveis, declará-los [privada](../../../visual-basic/language-reference/modifiers/private.md) para que nenhum outro código possa acessá-los.  
  
- **Criptografia.** Store todos os dados confidenciais em formato criptografado em vez de em texto sem formatação. Se alguma forma, código mal-intencionado obtiver acesso a área da memória, é mais difícil fazer uso dos dados. A criptografia também é útil se for necessário serializar os dados confidenciais.  
  
- **A redefinição.** Quando a classe, estrutura ou módulo definindo a propriedade está sendo finalizado, redefina os dados confidenciais para os valores padrão ou outros valores sem sentido. Isso proporciona proteção extra, quando a área da memória é liberada para acesso geral.  
  
- **Persistência.** Não mantêm todos os dados confidenciais, por exemplo, no disco, se você puder evitá-lo. Além disso, não escreva quaisquer dados confidenciais na área de transferência.  
  
 O `WriteOnly` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
