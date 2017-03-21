---
title: WriteOnly (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- WriteOnly
- vb.WriteOnly
dev_langs:
- VB
helpviewer_keywords:
- write-only properties
- WriteOnly keyword
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: 16
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
ms.openlocfilehash: 983ffecc1b8b5d406abefb254a05f2f415676866
ms.lasthandoff: 03/13/2017

---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Especifica que uma propriedade pode ser gravada mas não lida.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="rules"></a>Regras  
 **Contexto de declaração.** Você pode usar `WriteOnly` somente no nível de módulo. Isso significa que o contexto da declaração para um `WriteOnly` propriedade deve ser uma classe, estrutura ou módulo e não pode ser um arquivo fonte, namespace ou procedimento.  
  
 Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.  
  
## <a name="when-to-use-writeonly"></a>Quando usar WriteOnly  
 Às vezes você deseja ser capaz de definir um valor mas não descobrir o que é o código consumidor. Por exemplo, dados confidenciais, como um CPF ou uma senha, precisam ser protegido contra o acesso por qualquer componente que não definido. Nesses casos, você pode usar um `WriteOnly` propriedade para definir o valor.  
  
> [!IMPORTANT]
>  Quando você define e usa um `WriteOnly` propriedade, considere as seguintes medidas de proteção adicionais:  
  
-   **Substituindo.** Se a propriedade for um membro de uma classe, permitir que ele seja o padrão [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não o declare `Overridable` ou `MustOverride`. Isso impede que uma classe derivada faça um acesso indesejado através de uma substituição.  
  
-   **Nível de acesso.** Se você mantiver dados confidenciais a propriedade em uma ou mais variáveis, declare-las [particular](../../../visual-basic/language-reference/modifiers/private.md) para que nenhum outro código possa acessá-los.  
  
-   **Criptografia.** Armazene todos os dados confidenciais em formato criptografado em vez de em texto sem formatação. Se o código mal-intencionado de alguma maneira obtiver acesso à área de memória, é mais difícil fazer uso dos dados. A criptografia também é útil se for necessário serializar os dados confidenciais.  
  
-   **A redefinição.** Quando a classe, estrutura ou módulo definindo a propriedade está sendo finalizado, redefina os dados confidenciais para valores padrão ou outros valores sem sentido. Isso proporciona proteção extra quando essa área da memória é liberada para acesso geral.  
  
-   **Persistência.** Não mantenha quaisquer dados confidenciais, por exemplo, no disco, se você puder evitá-lo. Além disso, não escreva quaisquer dados confidenciais na área de transferência.  
  
 O `WriteOnly` modificador pode ser usado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Consulte também  
 [Somente leitura](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Privado](../../../visual-basic/language-reference/modifiers/private.md)   
 [Palavras-chave](../../../visual-basic/language-reference/keywords/index.md)
