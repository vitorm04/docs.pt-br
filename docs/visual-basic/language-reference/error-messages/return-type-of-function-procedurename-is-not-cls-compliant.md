---
title: "O tipo de retorno da fun&#231;&#227;o &#39;&lt;procedurename&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS | Microsoft Docs"
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
  - "bc40027"
  - "vbc40027"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40027"
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# O tipo de retorno da fun&#231;&#227;o &#39;&lt;procedurename&gt;&#39; n&#227;o &#233; compat&#237;vel com CLS
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Um procedimento `Function` está marcado como `<CLSCompliant(True)>` mas retorna um tipo que está marcado como `<CLSCompliant(False)>`, não está marcado, ou não se qualifica porque ele é um tipo incompatível.  
  
 Para um procedimento para ser compatível com o [Independência da linguagem e componentes independentes da linguagem](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\), ele deve usar somente tipos compatíveis com CLS.  Isso se aplica aos tipos de parâmetros, o tipo de retorno e os tipos de todas as suas variáveis locais.  
  
 Os seguintes tipos de dados [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não são compatíveis com CLS:  
  
-   [Tipo de dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Tipo de dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Tipo de dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Tipo de dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Quando você aplica o <xref:System.CLSCompliantAttribute> a um elemento de programação, você define o parâmetro `isCompliant` do atributo para `True` ou `False` para indicar compatibilidade ou incompatibilidade.  Não há padrão para este parâmetro, e você deve fornecer um valor.  
  
 Se você não aplicar o <xref:System.CLSCompliantAttribute> a um elemento, ele vai ser considerado incompatível.  
  
 Por padrão, essa é uma mensagem de aviso.  Para informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **Identificação do erro:**  BC40027  
  
### Para corrigir este erro  
  
-   Se o procedimento `Function` deve retornar esse tipo específico, remova o <xref:System.CLSCompliantAttribute>.  O procedimento não pode ser compatível com CLS.  
  
-   Se o procedimento `Function` deve ser compatível com CLS, altere o tipo de retorno para o tipo mais próximo compatível com CLS.  Por exemplo, no lugar de `UInteger` você poderá usar `Integer` se você não precisar o intervalo de valores acima 2.147.483.647.  Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
-   Se você estiver interfaceando com objetos de automação ou COM, tenha em mente que alguns tipos têm larguras de dados diferentes do que em [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Por exemplo, `int` é geralmente 16 bits em outros ambientes.  Se você estiver retornando um inteiro de 16 bits para tal um componente, declare\-o como `Short` em vez de `Integer` no seu código gerenciado [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
## Consulte também  
 [\<PAVE OVER\> Writing CLS\-Compliant Code](http://msdn.microsoft.com/pt-br/4c705105-69a2-4e5e-b24e-0633bc32c7f3)