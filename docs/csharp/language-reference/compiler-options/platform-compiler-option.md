---
title: "/platform (C# Compiler Options) | Microsoft Docs"
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
  - "/platform"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "platform compiler option [C#]"
  - "-platform compiler option [C#]"
  - "/platform compiler option [C#]"
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
caps.handback.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /platform (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Especifica qual versão do Common Language Runtime \(CLR\) pode executar o assembly.  
  
## Sintaxe  
  
```  
/platform:string  
```  
  
#### Parâmetros  
 `string`  
 anycpu \(padrão\), anycpu32bitpreferred, BRAÇO x86, x64, ou Itanium.  
  
## Comentários  
  
-   **anycpu** \(padrão\) cria seu assembly para executar em qualquer plataforma.  O aplicativo é executado como um processo de 64 bits sempre que possível e reverte para de 32 bits quando apenas esse modo está disponível.  
  
-   O **anycpu32bitpreferred** compila o assembly para ser executado em qualquer plataforma.  Seu aplicativo for executado no modo de 32 bits nos sistemas que oferecem suporte a aplicativos de 64 bits e de 32 bits.  Você pode especificar essa opção apenas para os projetos que visam o.NET Framework 4.5.  
  
-   **ARM** cria seu assembly para execução em um computador que tenha um processador avançada \(ARM\) do computador de RISC.  
  
-   O **x64** compila o assembly para ser executado pelo Common Language Runtime de 64 bits em um computador que oferece suporte ao conjunto de instruções de AMD64 ou EM64T  
  
-   **x86** cria seu assembly a ser executado pelo de 32 bits, x86\-compatible Common Language Runtime.  
  
-   **Itanium** cria seu assembly a ser executado por Common Language Runtime de 64 bits em um computador com um processador Itanium.  
  
 Em um sistema operacional Windows de 64 bits:  
  
-   Os assemblies compilados com **\/platform:x86** são executados em CLR de 32 bits executando sob WOW64.  
  
-   UMA DLL compilado com **\/platform:anycpu** é executado no CLR que o processo em que é carregado.  
  
-   Os executáveis que são compilados com **\/platform:anycpu** são executados em CLR de 64 bits.  
  
-   Os executáveis compilados com **\/platform:anycpu32bitpreferred** são executados em CLR de 32 bits.  
  
 Defina de **anycpu32bitpreferred** é válido somente para os arquivos executáveis \(.EXE\), e requer o.NET Framework 4.5.  
  
 Para obter mais informações sobre como desenvolver um aplicativo executar em um sistema operacional Windows de 64 bits, consulte [Aplicativos de 64 bits](../Topic/64-bit%20Applications.md).  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** para o projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Modifique a propriedade de **Destino da Plataforma** e, para projetos que visam o.NET Framework 4.5, marque ou desmarque a caixa de seleção de **Preferir 32 bits** .  
  
 **Observação**  
 **\/platform** não está disponível no ambiente de desenvolvimento no Visual C \# express.  
  
 Para obter informações sobre como definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>.  
  
## Exemplo  
 O exemplo a seguir mostra como usar a opção de **\/platform** especificar que o aplicativo deve ser executado por CLR de 64 bits em um sistema operacional Windows de 64 bits.  
  
```  
csc /platform:anycpu filename.cs  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)