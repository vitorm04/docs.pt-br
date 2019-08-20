---
title: 'Como: Configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF'
ms.date: 03/30/2017
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
ms.openlocfilehash: 3a9bf79a9d505fef53b62cb589920adcf95ae92a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611495"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Como: Configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF

Você pode implantar um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo da maioria dos servidores Web, desde que eles estejam configurados com os tipos de MIME (Multipurpose Internet Mail Extensions) apropriados. Por padrão, o Microsoft Serviços de Informações da Internet (IIS) 7,0 é configurado com esses tipos MIME, mas o Microsoft Serviços de Informações da Internet (IIS) 5,0 e o Microsoft Serviços de Informações da Internet (IIS) 6,0 não são.

Este tópico descreve como configurar o Microsoft serviços de informações da Internet (IIS) 5,0 e o Microsoft serviços de informações da Internet (IIS) 6,0 para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implantar aplicativos.

> [!NOTE]
> Você pode verificar a cadeia de caracteres UserAgent no registro para determinar se um sistema tem .NET Framework instalado. Para obter detalhes e um script que examina a cadeia de caracteres UserAgent para determinar se o .NET Framework está instalado em um sistema, consulte [detectar se o .NET Framework 3,0 está instalado](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Ajustar a configuração de expiração de conteúdo

É recomendável ajustar a configuração de expiração de conteúdo para 1 minuto. O procedimento a seguir descreve como fazer isso com o IIS.

1. Clique no menu **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador dos ISS (Serviços de Informações da Internet)** . Você também pode iniciar este aplicativo da linha de comando com “%SystemRoot%\system32\inetsrv\iis.msc”.

2. Expanda a árvore do IIS até encontrar o nó do **site da Web padrão** .

3. Clique com o botão direito do mouse em **Site da Web padrão** e selecione **Propriedades** no menu de contexto.

4. Selecione a guia **Cabeçalhos HTTP** e clique em “Habilitar expiração de conteúdo”.

5. Defina o conteúdo para expirar após um minuto.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>Registrar os tipos MIME e extensões de arquivo

Você deve registrar vários tipos MIME e extensões de arquivo para que o navegador no sistema do cliente possa carregar o manipulador correto. Você precisa adicionar os seguintes tipos:

|Extensão|Tipo MIME|
|---------------|---------------|
|.manifest|application/manifest|
|.xaml|application/xaml+xml|
|.application|application/x-ms-application|
|.xbap|application/x-ms-xbap|
|.deploy|application/octet-stream|
|.xps|application/vnd.ms-xpsdocument|

> [!NOTE]
> Você não precisa registrar tipos MIME ou extensões de arquivo em sistemas cliente. Eles são registrados automaticamente quando você instala o Microsoft .NET Framework.

O exemplo a seguir do Microsoft Visual Basic Scripting Edition (VBScript) adiciona automaticamente os tipos MIME necessários ao IIS. Para usar o script, copie o código para um arquivo .vbs no seu servidor. Em seguida, execute o script executando o arquivo na linha de comando ou clicando duas vezes no arquivo em [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].

```vb
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

' Get the MimeMap object
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
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> A execução desse script várias vezes cria várias entradas de mapa MIME na metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0.

Depois de executar esse script, você não poderá ver tipos MIME adicionais do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0 Microsoft Management Console (MMC). No entanto, esses tipos MIME foram adicionados à metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0. O script a seguir exibirá todos os tipos de MIME na metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0.

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

Salve o script como um arquivo `.vbs` (por exemplo, `DiscoverIISMimeTypes.vbs`) e execute-o no prompt de comando usando o seguinte comando:

```console
cscript DiscoverIISMimeTypes.vbs
```
