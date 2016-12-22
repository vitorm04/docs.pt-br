---
title: "/keycontainer (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/keycontainer"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/keycontainer compiler option [C#]"
  - "keycontainer compiler option [C#]"
  - "-keycontainer compiler option [C#]"
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /keycontainer (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica o nome do contêiner chave criptográfica.  
  
## Sintaxe  
  
```  
/keycontainer:string  
```  
  
## Arguments  
 `string`  
 O nome do contêiner de chave de nome forte.  
  
## Comentários  
 Quando a opção de **\/keycontainer** é usada, o compilador criar um componente compartilhável inserindo uma chave pública do contêiner especificado no manifesto do assembly e assinar o assembly final com a chave privada.  Para gerar um arquivo de chave, digite o sn \- k `file` na linha de comando. sn \- i instala o par de chaves em um contêiner.  
  
 Se você compila com [\/target: módulo](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), o nome do arquivo da chave será realizado no módulo e inserida no assembly quando você cria esse módulo em um assembly com [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Você também pode especificar esta opção como um atributo personalizado \(<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>\) no código\-fonte para qualquer módulo de linguagem intermediária Microsoft \(MSIL\).  
  
 Você também pode transmitir suas informações de criptografia ao compilador com [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md).  Use [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se desejar que a chave pública adicionada ao manifesto do assembly mas quiser atrasar assinar o assembly até ser testado.  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nome forte](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) e [Atrasando a assinatura de um assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Essa opção de compilador não está disponível no ambiente de desenvolvimento do Visual Studio.  
  
 Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)