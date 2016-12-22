---
title: "O tipo de membro &#39;&lt;membername&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc40025"
  - "vbc40025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40025"
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo de membro &#39;&lt;membername&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O tipo de dados especificado para este membro não é parte do [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\).  Isso não é um erro no seu componente, pois o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] e [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suportam este tipo de dados.  No entanto, outro componente escrito em estritamente código compatível com CLS pode não oferecer suporte a esse tipo de dados.  Tal componente não poderá interagir com êxito com seu componente.  
  
 Os seguintes tipos de dados [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não são compatíveis com CLS:  
  
-   [Tipo de dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Por padrão, essa é uma mensagem de aviso.  Para maiores informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40025  
  
### Para corrigir este erro  
  
-   Se seu componente somente tem interface com outros componentes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)],ou não tem interface com quaisquer outros componentes, você não precisará alterar nada.  
  
-   Se você estiver interfaceando com um componente não gravado para o [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)],talvez seja possível determinar, através de reflexão ou da documentação, se ele suporta este tipo de dados.  Em caso afirmativo, você não precisará alterar nada.  
  
-   Se você está interfaceando com um componente que não suporte este tipo de dados, você deverá substituí\-lo com o tipo mais próximo compatível com CLS.  Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar o intervalo de valores acima 2.147.483.647.  Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver interfaceando com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que em [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Por exemplo, `uint` é geralmente 16 bits em outros ambientes.  Se você estiver passando um argumento de 16 bits para tal um componente, declare\-o como `UShort` em vez de `UInteger` no seu código [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gerenciado.  
  
## Consulte também  
 [Reflexão](../Topic/Reflection%20in%20the%20.NET%20Framework.md)   
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)