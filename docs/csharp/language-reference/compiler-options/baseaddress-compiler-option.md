---
title: "/baseaddress (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dllbase"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "baseaddress compiler option [C#]"
  - "/baseaddress compiler option [C#]"
  - "-baseaddress compiler option [C#]"
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /baseaddress (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção de **\/baseaddress** permite especificar o endereço base preferência no qual carregar uma DLL.  Para obter mais informações sobre quando e por que usar essa opção, consulte [Melhorando o tempo de inicialização do aplicativo](http://go.microsoft.com/fwlink/?LinkId=107043) e [WebLog de Larry Osterman](http://go.microsoft.com/fwlink/?LinkId=107044).  
  
## Sintaxe  
  
```  
/baseaddress:address  
```  
  
## Arguments  
 `address`  
 O endereço base para a DLL.  Este endereço pode ser especificado como um número decimal, hexadecimal, ou octal.  
  
## Comentários  
 O endereço base padrão para uma DLL é definido pelo .NET Framework Common Language Runtime.  
  
 Lembre\-se de que as palavras de ordem mais inferior neste endereço serão arredondadas.  Por exemplo, se você especificar 0x11110001, será arredondado para 0x11110000.  
  
 Para concluir o processo de assinatura para uma DLL, use SN.EXE com a opção \- R.  
  
### Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página de **Propriedades** do projeto.  
  
2.  Clique na página de propriedades de **Compilar** .  
  
3.  Clique no botão de **Avançado** .  
  
4.  Modifique a propriedade de **Endereço básico de DLL** .  
  
     Para definir programaticamente essa opção do compilador, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.  
  
## Consulte também  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)