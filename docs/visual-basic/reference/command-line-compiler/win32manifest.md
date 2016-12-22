---
title: "/win32manifest (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Opção de compilador /win32manifest [Visual Basic]"
  - "Opção de compilador win32manifest [Visual Basic]"
  - "Opção de compilador -win32manifest [Visual Basic]"
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /win32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Identifica o arquivo de manifesto do aplicativo Win32 definido pelo usuário para ser incorporado em um arquivo executável  portátil \(PE\) de um projeto.  
  
## Sintaxe  
  
```  
/win32manifest: fileName  
```  
  
## Argumentos  
  
|||  
|-|-|  
|Termo|Definição|  
|`fileName`|O caminho do arquivo de manifesto personalizado.|  
  
## Comentários  
 Por padrão, o compilador Visual Basic incorpora um manifesto de aplicativo que especifica um nível de execução necessário como asInvoker.  Cria o manifesto no mesmo diretório em que o arquivo executável é criado, normalmente o diretório bin\\Debug ou bin\\Release que o Visual Studio é utilizado.  Se quiser fornecer um manifesto personalizado, por exemplo para especificar um nível de execução necessário de highestAvailable ou requireAdministrator, use essa opção para especificar o nome do arquivo.  
  
> [!NOTE]
>  Esta opção e a opção [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) são mutuamente exclusivas.  Se você tentar usar ambas as expressões na mesma linha de comando, será gerado um erro de compilação.  
  
 Um aplicativo que não tem manifesto de aplicativo que especifica um nível de execução necessário estará sujeita a virtualização de arquivo\/registro sob a ferramenta de Controle de Conta de Usuário no Windows Vista  Para mais informações sobre virtualização, consulte [Implantação do ClickOnce no Windows Vista](/visual-studio/deployment/clickonce-deployment-on-windows-vista).  
  
 Seu aplicativo estará sujeito a virtualização se alguma das condições a seguir for satisfeita:  
  
1.  Usa a opção `/nowin32manifest` e não será necessário fornecer um manifest em um passo depois da compilação ou como parte de um arquivo Windows Resource \(.res\) , usando a opção `/win32resource`.  
  
2.  Você fornece um manifesto personalizado que não especifica um nível de execução necessário.  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] cria um arquivo padrão de manifesto e o armazena nos diretórios de depuração e versão junto do arquivo executável.  Você pode exibir ou editar o arquivo app. manifest padrão clicando em  **Exibir configurações UAC** sobre o  **aplicativo** guia no Project Designer. Para obter mais informações, consulte [Página de Aplicativo, Designer de Projeto \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic).  
  
 Você pode fornecer o manifesto da aplicação como um passo personalizado pós\-compilação como parte de um arquivo de recurso Win32 através da opção `/nowin32manifest`.  Use essa mesma opção se quiser que sua apliacação esteja sujeita a virtualização de arquivo ou registro no Windows Vista.  Isso irá prevenir que o compilador crie e incorpore um manifesto padrão no arquivo PE.  
  
## Exemplo  
 O exemplo a seguir mostra o manisfesto padrão que o compilador Visual Basic insere em um PE.  
  
> [!NOTE]
>  O compilador insere um nome padrão de aplicativo MyApplication.app no manifesto XML.  Essa é uma solução para habilitar aplicativos para rodarem em Windows Server 2003 Service Pack 3.  
  
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
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)