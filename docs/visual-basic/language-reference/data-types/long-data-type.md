---
title: "Tipo de dados Long (Visual Basic) | Microsoft Docs"
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
  - "vb.Long"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "caractere de tipo identificador &"
  - "tipos de dados [Visual Basic], atribuindo"
  - "tipos de dados [Visual Basic], integral"
  - "caracteres de tipo identificador, &"
  - "números inteiros"
  - "números inteiros, tipos de dados"
  - "números inteiros, tipos"
  - "tipos de dados integrais"
  - "caractere de tipo literal L"
  - "caracteres de tipo literal, L"
  - "tipo de dados Long"
  - "palavra-chave Long"
  - "números, inteiro"
  - "números, inteiro"
  - "números inteiros"
ms.assetid: b4770c34-1804-4f8c-b512-c10b0893e516
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tipo de dados Long (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Suspensões assinado inteiros do 64 bits \(8 bytes\) cujo valor varia de \-9.223.372.036.854.775.808 através de 9.223.372.036.854.775.807 \(9.2... E \+ 18\).  
  
## Comentários  
 Use o `Long` o tipo de dados para conter números inteiros que são grandes demais para caber na `Integer` tipo de dados.  
  
 O valor padrão para `Long` é 0.  
  
## Dicas de Programação  
  
-   **Considerações de interoperabilidade.** Se você está em uma interface com componentes não escritos para o.NET Framework, por exemplo automação ou COM objetos, lembre\-se que `Long` tem uma largura de dados diferentes \(32 bits\) em outros ambientes.  Se você estiver passando um argumento de 32 bits para tal componente, declare\-o como `Integer` em vez de `Long` no seu novo Visual Basic.  
  
     Além disso, automação não oferece suporte a inteiros de 64 bits no Windows 95, Windows 98, Windows ME ou Windows 2000.  Você não pode passar um Visual Basic `Long` argumento para um componente de automação nesses sistemas operacionais.  
  
-   **Tipos de dados.** The `Long` data type widens to `Decimal`, `Single`, or `Double`.  Isto significa que você pode converter um `Long` para qualquer um desses tipos sem a ocorrência de um erro <xref:System.OverflowException?displayProperty=fullName>.  
  
-   **Caracteres de tipo.** Acrescentando o caractere de tipo literal `L` para um literal, força\-o para o `Long` tipo de dados.  Acrescentar o caractere de tipo identificador `&` a qualquer identificador o força ao tipo `Long`.  
  
-   **Tipos de Framework.** O tipo correspondente na.NET Framework é o <xref:System.Int64?displayProperty=fullName> estrutura.  
  
## Consulte também  
 <xref:System.Int64>   
 [Tipos de dados](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Tipo de dados inteiro](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [Tipo de dados curto](../../../visual-basic/language-reference/data-types/short-data-type.md)   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)