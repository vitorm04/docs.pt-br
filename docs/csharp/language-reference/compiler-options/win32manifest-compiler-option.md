---
title: "/win32manifest (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/win32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/win32manifest compiler option [C#]"
  - "win32manifest compiler option [C#]"
  - "-win32manifest compiler option [C#]"
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /win32manifest (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Use a opção de **\/win32manifest** especificar um arquivo de manifesto de aplicativo definida pelo usuário do Win32 a ser inserido no arquivo executável portátil \(PE\) de um projeto.  
  
## Sintaxe  
  
```  
/win32manifest: filename  
```  
  
## Arguments  
 `filename`  
 O nome e o local do arquivo de manifesto personalizado.  
  
## Comentários  
 Por padrão, o compilador de [!INCLUDE[csharp_current_short](../../../csharp/language-reference/compiler-options/includes/csharp_current_short_md.md)] inserir um manifesto de aplicativo que especifica uma execução solicitada em nível de asInvoker “.” Criam o manifesto na mesma pasta em que o executável é criado, normalmente o \\ bin \\ debug ou pasta bin \\ de versão de linha quando você usa o Visual Studio.  Se você desejar fornecer um manifesto personalizado, por exemplo para especificar uma execução solicitada em nível de “highestAvailable” ou “,” requireAdministrator use essa opção para especificar o nome do arquivo.  
  
> [!NOTE]
>  Esta opção e a opção [\/win32res \(Import a Win32 Resource File\)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) são mutuamente exclusivas.  Se você tentar usar ambas as opções na mesma linha de comando você obterá um erro de compilação.  
  
 Um aplicativo que não tem manifesto de aplicativo que especifica um nível de execução necessário estará sujeita a virtualização de arquivo\/registro sob a ferramenta de Controle de Conta de Usuário no Windows Vista  Para obter mais informações sobre de virtualização, consulte [O histórico do desenvolvedor do Windows Vista: Requisitos de desenvolvimento de aplicativos do Windows Vista para Controle de Conta de Usuário \(UAC\)](http://go.microsoft.com/fwlink/?LinkId=95452).  
  
 Seu aplicativo será sujeito a virtualização se qualquer uma destas condições for verdadeira:  
  
-   Usa a opção **\/nowin32manifest** e não será necessário fornecer um manifest em um passo depois da compilação ou como parte de um arquivo Windows Resource \(.res\) , usando a opção **\/win32res**.  
  
-   Você fornece um manifesto personalizado que não especifica um nível de execução necessário.  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] cria um arquivo padrão de manifesto e o armazena nos diretórios de depuração e versão junto do arquivo executável.  Você pode adicionar um manifesto personalizado criando um em qualquer editor de texto e adicionando o arquivo ao projeto.  Se preferir, clique com o botão direito do mouse no ícone de **Projeto** em **Gerenciador de Soluções**, clique em **Adicionar novo item**, e clique em **Arquivo de Manifesto do Aplicativo**.  Depois de adicionar o novo ou arquivo de manifesto existente, aparecerá em **Manifesto** remove para baixo na lista.  Para obter mais informações, consulte [Página Aplicativo, Designer de Projeto \(C\#\)](/visual-studio/ide/reference/application-page-project-designer-csharp).  
  
 Você pode fornecer o manifesto da aplicação como um passo personalizado pós\-compilação como parte de um arquivo de recurso Win32 através da opção [\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md).  Use essa mesma opção se quiser que sua aplicação esteja sujeita a virtualização de arquivo ou registro no Windows Vista.  Isso evitará que o compilador criar e insira um manifesto padrão no arquivo executável portátil de \(PE\).  
  
## Exemplo  
 O exemplo a seguir mostra o manifesto padrão que as inserções do compilador do Visual C \# em um PE.  
  
> [!NOTE]
>  O compilador insere um nome de aplicativo padrão “MyApplication.app” no XML.  Essa é uma solução para habilitar aplicativos para rodarem em Windows Server 2003 Service Pack 3.  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## Consulte também  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)   
 [Como modificar as propriedades de projeto e as definições de configuração](http://msdn.microsoft.com/pt-br/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)