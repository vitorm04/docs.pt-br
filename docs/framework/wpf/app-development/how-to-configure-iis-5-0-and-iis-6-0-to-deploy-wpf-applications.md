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
ms.openlocfilehash: 3179679abcf32e40374c7f02e64466a326a73195
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69013019"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Como: Configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF

Você pode implantar um [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativo da maioria dos servidores Web, desde que eles estejam configurados com os tipos de MIME (Multipurpose Internet Mail Extensions) apropriados. Por padrão, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] o é configurado com esses tipos MIME, [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] mas [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] e não.

Este tópico descreve como configurar [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] e [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] para implantar aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

> [!NOTE]
> Você pode verificar a cadeia de caracteres UserAgent no registro para determinar se um sistema tem .NET Framework instalado. Para obter detalhes e um script que examina a cadeia de caracteres UserAgent para determinar se o .NET Framework está instalado em um sistema, consulte [detectar se o .NET Framework 3,0 está instalado](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Ajustar a configuração de expiração de conteúdo

É recomendável ajustar a configuração de expiração de conteúdo para 1 minuto. O procedimento a seguir descreve como fazer isso com [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].

1. Clique no menu **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador dos ISS (Serviços de Informações da Internet)** . Você também pode iniciar este aplicativo da linha de comando com “%SystemRoot%\system32\inetsrv\iis.msc”.

2. Expanda a árvore [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] até localizar o nó **Site da Web Padrão**.

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

O exemplo a seguir do Microsoft Visual Basic Scripting Edition (VBScript) adiciona automaticamente os tipos MIME [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]necessários ao. Para usar o script, copie o código para um arquivo .vbs no seu servidor. Em seguida, execute o script executando o arquivo na linha de comando ou clicando duas vezes no arquivo em [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].

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
> Executar esse script várias vezes cria várias entradas de mapa MIME na [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabase [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ou.

Depois de executar esse script, talvez você não veja tipos MIME adicionais no [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ou [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] no console de gerenciamento Microsoft (MMC). No entanto, esses tipos MIME foram adicionados à [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] metabase [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] ou. O script a seguir exibirá todos os tipos de MIME [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] na [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metabase ou.

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
