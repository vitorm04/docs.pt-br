---
title: Como configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edc4bc985f7117dc66d29053d62a283d67b01a85
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Como configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF
Você pode implantar um aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] da maioria dos servidores Web, desde que eles sejam configurados com os devidos tipos [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)]. Por padrão, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] é configurado com esses tipos [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)], mas [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] e [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] não são.  
  
 Este tópico descreve como configurar [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] e [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] para implantar aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
  
> [!NOTE]
>  Você pode verificar o *UserAgent* cadeia de caracteres no registro para determinar se um sistema tem o .NET Framework instalado. Para obter detalhes e um script que examina o *UserAgent* cadeia de caracteres para determinar se o .NET Framework é instalado em um sistema, consulte [detectar se o .NET Framework 3.0 está instalado](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md).  
  
<a name="content_expiration"></a>   
## <a name="adjust-the-content-expiration-setting"></a>Ajustar a configuração de expiração de conteúdo  
 É recomendável ajustar a configuração de expiração de conteúdo para 1 minuto. O procedimento a seguir descreve como fazer isso com [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].  
  
1.  Clique no menu **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador dos ISS (Serviços de Informações da Internet)**. Você também pode iniciar este aplicativo da linha de comando com “%SystemRoot%\system32\inetsrv\iis.msc”.  
  
2.  Expanda a árvore [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] até localizar o nó **Site da Web Padrão**.  
  
3.  Clique com o botão direito do mouse em **Site da Web padrão** e selecione **Propriedades** no menu de contexto.  
  
4.  Selecione a guia **Cabeçalhos HTTP** e clique em “Habilitar expiração de conteúdo”.  
  
5.  Defina o conteúdo para expirar após um minuto.  
  
<a name="register_mime_types"></a>   
## <a name="register-mime-types-and-file-extensions"></a>Registrar os tipos MIME e extensões de arquivo  
 Você deve registrar vários tipos [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] e extensões de arquivo para que o navegador no sistema cliente possa carregar o manipulador correto. Você precisa adicionar os seguintes tipos:  
  
|Extensão|Tipo MIME|  
|---------------|---------------|  
|.manifest|application/manifest|  
|.xaml|application/xaml+xml|  
|.application|application/x-ms-application|  
|.xbap|application/x-ms-xbap|  
|.deploy|application/octet-stream|  
|.xps|application/vnd.ms-xpsdocument|  
  
> [!NOTE]
>  Você não precisa registrar tipos ou extensões de arquivo [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] em sistemas cliente. Eles são registrados automaticamente quando você instala o Microsoft .NET Framework.  
  
 O exemplo de Microsoft Visual Basic Scripting Edition (VBScript) a seguir adiciona automaticamente o necessário [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] tipos [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]. Para usar o script, copie o código para um arquivo .vbs no seu servidor. Em seguida, execute o script executando o arquivo na linha de comando ou clicando duas vezes no arquivo em [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].  
  
```  
' This script adds the necessary Windows Presentation Foundation MIME types   
' to an IIS Server.  
' To use this script, just double-click or execute it from a command line.  
' Running this script multiple times results in multiple entries in the IIS MimeMap.  
  
Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec  
Const ADS_PROPERTY_UPDATE = 2   
  
' Set the MIME types to be added  
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _  
    "application/xaml+xml", ".application", "application/x-ms-application", _  
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _  
    ".xps", "application/vnd.ms-xpsdocument")   
  
' Get the mimemap object   
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")  
  
' Call AddMimeType for every pair of extension/MIME type  
For counter = 0 to UBound(MimeTypesToAddArray) Step 2  
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)  
Next  
  
' Create a Shell object  
Set WshShell = CreateObject("WScript.Shell")  
  
' Stop and Start the IIS Service  
Set oExec = WshShell.Exec("net stop w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = WshShell.Exec("net start w3svc")  
Do While oExec.Status = 0  
    WScript.Sleep 100  
Loop  
  
Set oExec = Nothing  
  
' Report status to user  
WScript.Echo "Windows Presentation Foundation MIME types have been registered."  
  
' AddMimeType Sub  
Sub AddMimeType (Ext, MType)  
  
    ' Get the mappings from the MimeMap property.   
    MimeMapArray = MimeMapObj.GetEx("MimeMap")   
  
    ' Add a new mapping.   
    i = UBound(MimeMapArray) + 1   
    Redim Preserve MimeMapArray(i)   
    Set MimeMapArray(i) = CreateObject("MimeMap")   
    MimeMapArray(i).Extension = Ext   
    MimeMapArray(i).MimeType = MType   
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray  
    MimeMapObj.SetInfo  
  
End Sub  
```  
  
> [!NOTE]
>  Executar esse script várias vezes cria várias entradas de mapa [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] na metabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  
  
 Depois de executar esse script, você não poderá ver tipos [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] adicionais do [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)]. No entanto, esses tipos de [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] foram adicionados ao metabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)]. O script a seguir exibirá todos os tipos [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] no metabase [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)].  
  
```  
' This script lists the MIME types for an IIS Server.  
' To use this script, just double-click or execute it from a command line   
' by calling cscript.exe  
  
dim mimeMapEntry, allMimeMaps  
  
' Get the mimemap object.  
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")  
allMimeMaps = mimeMapEntry.GetEx("MimeMap")  
  
' Display the mappings in the table.  
For Each mimeMap In allMimeMaps  
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")  
Next  
```  
  
 Salve o script como um arquivo `.vbs` (por exemplo, `DiscoverIISMimeTypes.vbs`) e execute-o no prompt de comando usando o seguinte comando:  
  
 `cscript DiscoverIISMimeTypes.vbs`
