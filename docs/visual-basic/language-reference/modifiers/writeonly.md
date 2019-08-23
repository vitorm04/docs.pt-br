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
ms.openlocfilehash: 43507ac8e9b5843e8fa9496737a3d77b3a425a7f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963763"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Especifica que uma propriedade pode ser gravada, mas não lida.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
 **Contexto de declaração.** Você pode usar `WriteOnly` somente no nível do módulo. Isso significa que o contexto de Declaração `WriteOnly` para uma propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo de origem, namespace ou procedimento.  
  
 Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.  
  
## <a name="when-to-use-writeonly"></a>Quando usar WriteOnly  
 Às vezes, você quer que o código de consumo seja capaz de definir um valor, mas não descobrir o que ele é. Por exemplo, dados confidenciais, como um número de registro social ou uma senha, precisam ser protegidos do acesso por qualquer componente que não o definiu. Nesses casos, você pode usar uma `WriteOnly` propriedade para definir o valor.  
  
> [!IMPORTANT]
> Ao definir e usar uma `WriteOnly` Propriedade, considere as seguintes medidas de proteção adicionais:  
  
- **Sobrecarga.** Se a propriedade for um membro de uma classe, permita que ela seja padronizada como não [substituível](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não a `Overridable` Declare `MustOverride`ou. Isso impede que uma classe derivada faça acesso indesejado por meio de uma substituição.  
  
- **Nível de acesso.** Se você mantiver os dados confidenciais da propriedade em uma ou mais variáveis, declare-as como [particulares](../../../visual-basic/language-reference/modifiers/private.md) para que nenhum outro código possa acessá-las.  
  
- **Encripta.** Armazene todos os dados confidenciais em formato criptografado em vez de em texto sem formatação. Se um código mal-intencionado tiver acesso a essa área de memória, será mais difícil fazer o uso dos dados. A criptografia também é útil se for necessário serializar os dados confidenciais.  
  
- **Redefinir.** Quando a classe, a estrutura ou o módulo que define a propriedade está sendo encerrado, redefina os dados confidenciais para valores padrão ou para outros valores sem sentido. Isso fornece proteção extra quando essa área de memória é liberada para acesso geral.  
  
- **Persistência.** Não persista nenhum dado confidencial, por exemplo, no disco, se você puder evitá-lo. Além disso, não grave nenhum dado confidencial na área de transferência.  
  
 O `WriteOnly` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Privado](../../../visual-basic/language-reference/modifiers/private.md)
- [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
