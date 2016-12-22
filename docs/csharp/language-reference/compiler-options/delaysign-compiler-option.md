---
title: "/delaysign (C# Compiler Options) | Microsoft Docs"
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
  - "/delaysign"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-delaysign compiler option [C#]"
  - "delaysign compiler option [C#]"
  - "/delaysign compiler option [C#]"
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /delaysign (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Esta opção faz com que o compilador ao espaço de reserva no arquivo de saída de forma que uma assinatura digital seja adicionada posteriormente.  
  
## Sintaxe  
  
```  
/delaysign[ + | - ]  
```  
  
## Arguments  
 `+` &#124; `-`  
 Use **\/delaysign\-** se você desejar um assembly totalmente assinado.  Use **\/delaysign\+** se você só quiser colocar a chave pública no assembly.  O padrão é **\/delaysign\-**.  
  
## Comentários  
 A opção de **\/delaysign** não tem nenhum efeito a menos que usado com [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) ou [\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).  
  
 Quando você solicita um assembly totalmente assinado, o compilador o uso do arquivo que contém o manifesto do assembly \(metadados\) e os sinais que picam com a chave privada.  A assinatura digital resultante é armazenada no arquivo que contém o manifesto.  Quando um assembly é atraso assinado, o compilador não computa e não armazena a assinatura, mas o espaço das reservas no arquivo para que a assinatura poderá ser adicionado posteriormente.  
  
 Por exemplo, o uso **\/delaysign\+** permite que um verificador coloque o assembly no cache global.  Depois de teste, você pode totalmente assinar o assembly colocando a chave privada no assembly que usa o utilitário de [O vinculador de assembly](../Topic/Al.exe%20\(Assembly%20Linker\).md) .  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nome forte](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md) e [Atrasando a assinatura de um assembly](../Topic/Delay%20Signing%20an%20Assembly.md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** para o projeto.  
  
2.  Modifique a propriedade de **Somente sinal de atraso** .  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)