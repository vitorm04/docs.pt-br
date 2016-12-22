---
title: "WriteOnly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WriteOnly"
  - "vb.WriteOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "propriedades [Visual Basic], somente gravação"
  - "dados confidenciais"
  - "dados confidenciais, protegendo"
  - "Palavra-chave WriteOnly"
  - "propriedades somente gravação"
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WriteOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica que uma propriedade pode ser gravada mas não lida.  
  
## Comentários  
  
## Regras  
 **Contexto da Declaração.** Você pode usar `WriteOnly` somente no nível de módulo.  Isso significa que o contexto da declaração para uma propriedade `WriteOnly` deve ser uma classe, estrutura ou módulo e não um arquivo de código\-fonte, namespace ou procedimento.  
  
 Você pode declarar uma propriedade como `WriteOnly`, mas não uma variável.  
  
## Quando usar WriteOnly  
 Às vezes você deseja que o código consumidor seja capaz de definir um valor mas não descobrir o que ele é.  Por exemplo, dados confidenciais, como um CPF ou uma senha, precisam ser protegidos contra o acesso por qualquer componente que não os definiram.  Nesses casos, você pode usar uma propriedade `WriteOnly` para definir o valor.  
  
> [!IMPORTANT]
>  Quando você define e usa uma propriedade `WriteOnly`, considere as seguintes medidas de proteção adicionais:  
  
-   **Substituindo.** Se a propriedade for um membro de uma classe, permitir que ele seja o padrão [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)e não o declara `Overridable` ou `MustOverride`.  Isso impede que uma classe derivada faça um acesso indesejado através de uma substituição.  
  
-   **Nível de acesso.** Se você mantiver os dados confidenciais da propriedade em uma ou mais variáveis, declará\-los [Particular](../../../visual-basic/language-reference/modifiers/private.md) , de modo que nenhum outro código pode acessá\-los.  
  
-   **Criptografia.** Armazene todas os dados confidenciais em formato criptografado em vez de em texto sem\-formatação.  Se código mal\-intencionado de alguma maneira obtiver acesso à essa área de memória, é mais difícil fazer uso dos dados.  A criptografia também é útil se for necessário serializar os dados confidenciais.  
  
-   **Redefinindo.** Quando a classe, estrutura ou módulo definindo a propriedade está sendo finalizado, redefina os dados confidenciais para valores padrão ou outros valores sem\-sentido.  Isso proporciona proteção extra quando essa área da memória é liberada para acesso geral.  
  
-   **Persistência.** Não mantenha quaisquer dados confidenciais, em disco por exemplo, se você pode evitá\-lo.  Além disso, não grave nenhum dado confidencial na Área de transferência.  
  
 O modificador `WriteOnly` pode ser utilizado neste contexto:  
  
 [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Consulte também  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Particular](../../../visual-basic/language-reference/modifiers/private.md)   
 [Palavras\-chave](../../../visual-basic/language-reference/keywords/index.md)