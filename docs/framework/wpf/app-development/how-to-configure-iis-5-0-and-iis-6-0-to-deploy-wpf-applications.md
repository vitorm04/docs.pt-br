---
title: Como configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF
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
ms.openlocfilehash: a731dc49556a73c585c6201a80ea3ea77c15cb11
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124423"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a><span data-ttu-id="af284-102">Como configurar o IIS 5.0 e o IIS 6.0 para implantar aplicativos WPF</span><span class="sxs-lookup"><span data-stu-id="af284-102">How to: Configure IIS 5.0 and IIS 6.0 to Deploy WPF Applications</span></span>

<span data-ttu-id="af284-103">Você pode implantar um aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] da maioria dos servidores Web, desde que eles estejam configurados com os tipos de MIME (Multipurpose Internet Mail Extensions) apropriados.</span><span class="sxs-lookup"><span data-stu-id="af284-103">You can deploy a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application from most Web servers, as long as they are configured with the appropriate Multipurpose Internet Mail Extensions (MIME) types.</span></span> <span data-ttu-id="af284-104">Por padrão, o Microsoft Serviços de Informações da Internet (IIS) 7,0 é configurado com esses tipos MIME, mas o Microsoft Serviços de Informações da Internet (IIS) 5,0 e o Microsoft Serviços de Informações da Internet (IIS) 6,0 não são.</span><span class="sxs-lookup"><span data-stu-id="af284-104">By default, Microsoft Internet Information Services (IIS) 7.0 is configured with these MIME types, but Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 are not.</span></span>

<span data-ttu-id="af284-105">Este tópico descreve como configurar o Microsoft Serviços de Informações da Internet (IIS) 5,0 e o Microsoft Serviços de Informações da Internet (IIS) 6,0 para implantar aplicativos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af284-105">This topic describes how to configure Microsoft Internet Information Services (IIS) 5.0 and Microsoft Internet Information Services (IIS) 6.0 to deploy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span>

> [!NOTE]
> <span data-ttu-id="af284-106">Você pode verificar a cadeia de caracteres *UserAgent* no registro para determinar se um sistema tem .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="af284-106">You can check the *UserAgent* string in the registry to determine whether a system has .NET Framework installed.</span></span> <span data-ttu-id="af284-107">Para obter detalhes e um script que examina a cadeia de caracteres *UserAgent* para determinar se o .NET Framework está instalado em um sistema, consulte [detectar se o .NET Framework 3,0 está instalado](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span><span class="sxs-lookup"><span data-stu-id="af284-107">For details and a script that examines the *UserAgent* string to determine whether .NET Framework is installed on a system, see [Detect Whether the .NET Framework 3.0 Is Installed](how-to-detect-whether-the-net-framework-3-0-is-installed.md).</span></span>

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a><span data-ttu-id="af284-108">Ajustar a configuração de expiração de conteúdo</span><span class="sxs-lookup"><span data-stu-id="af284-108">Adjust the Content Expiration Setting</span></span>

<span data-ttu-id="af284-109">É recomendável ajustar a configuração de expiração de conteúdo para 1 minuto.</span><span class="sxs-lookup"><span data-stu-id="af284-109">You should adjust the content expiration setting to 1 minute.</span></span> <span data-ttu-id="af284-110">O procedimento a seguir descreve como fazer isso com o IIS.</span><span class="sxs-lookup"><span data-stu-id="af284-110">The following procedure outlines how to do this with IIS.</span></span>

1. <span data-ttu-id="af284-111">Clique no menu **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador dos ISS (Serviços de Informações da Internet)** .</span><span class="sxs-lookup"><span data-stu-id="af284-111">Click the **Start** menu, point to **Administrative Tools**, and click **Internet Information Services (IIS) Manager**.</span></span> <span data-ttu-id="af284-112">Você também pode iniciar este aplicativo da linha de comando com “%SystemRoot%\system32\inetsrv\iis.msc”.</span><span class="sxs-lookup"><span data-stu-id="af284-112">You can also launch this application from the command line with "%SystemRoot%\system32\inetsrv\iis.msc".</span></span>

2. <span data-ttu-id="af284-113">Expanda a árvore do IIS até encontrar o nó do **site da Web padrão** .</span><span class="sxs-lookup"><span data-stu-id="af284-113">Expand the IIS tree until you find the **Default Web site** node.</span></span>

3. <span data-ttu-id="af284-114">Clique com o botão direito do mouse em **Site da Web padrão** e selecione **Propriedades** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="af284-114">Right-click **Default Web site** and select **Properties** from the context menu.</span></span>

4. <span data-ttu-id="af284-115">Selecione a guia **Cabeçalhos HTTP** e clique em “Habilitar expiração de conteúdo”.</span><span class="sxs-lookup"><span data-stu-id="af284-115">Select the **HTTP Headers** tab and click "Enable Content Expiration".</span></span>

5. <span data-ttu-id="af284-116">Defina o conteúdo para expirar após um minuto.</span><span class="sxs-lookup"><span data-stu-id="af284-116">Set the content to expire after 1 minute.</span></span>

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a><span data-ttu-id="af284-117">Registrar os tipos MIME e extensões de arquivo</span><span class="sxs-lookup"><span data-stu-id="af284-117">Register MIME Types and File Extensions</span></span>

<span data-ttu-id="af284-118">Você deve registrar vários tipos MIME e extensões de arquivo para que o navegador no sistema do cliente possa carregar o manipulador correto.</span><span class="sxs-lookup"><span data-stu-id="af284-118">You must register several MIME types and file extensions so that the browser on the client's system can load the correct handler.</span></span> <span data-ttu-id="af284-119">Você precisa adicionar os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="af284-119">You need to add the following types:</span></span>

|<span data-ttu-id="af284-120">Extensão</span><span class="sxs-lookup"><span data-stu-id="af284-120">Extension</span></span>|<span data-ttu-id="af284-121">Tipo MIME</span><span class="sxs-lookup"><span data-stu-id="af284-121">MIME Type</span></span>|
|---------------|---------------|
|<span data-ttu-id="af284-122">.manifest</span><span class="sxs-lookup"><span data-stu-id="af284-122">.manifest</span></span>|<span data-ttu-id="af284-123">application/manifest</span><span class="sxs-lookup"><span data-stu-id="af284-123">application/manifest</span></span>|
|<span data-ttu-id="af284-124">.xaml</span><span class="sxs-lookup"><span data-stu-id="af284-124">.xaml</span></span>|<span data-ttu-id="af284-125">application/xaml+xml</span><span class="sxs-lookup"><span data-stu-id="af284-125">application/xaml+xml</span></span>|
|<span data-ttu-id="af284-126">.application</span><span class="sxs-lookup"><span data-stu-id="af284-126">.application</span></span>|<span data-ttu-id="af284-127">application/x-ms-application</span><span class="sxs-lookup"><span data-stu-id="af284-127">application/x-ms-application</span></span>|
|<span data-ttu-id="af284-128">.xbap</span><span class="sxs-lookup"><span data-stu-id="af284-128">.xbap</span></span>|<span data-ttu-id="af284-129">application/x-ms-xbap</span><span class="sxs-lookup"><span data-stu-id="af284-129">application/x-ms-xbap</span></span>|
|<span data-ttu-id="af284-130">.deploy</span><span class="sxs-lookup"><span data-stu-id="af284-130">.deploy</span></span>|<span data-ttu-id="af284-131">application/octet-stream</span><span class="sxs-lookup"><span data-stu-id="af284-131">application/octet-stream</span></span>|
|<span data-ttu-id="af284-132">.xps</span><span class="sxs-lookup"><span data-stu-id="af284-132">.xps</span></span>|<span data-ttu-id="af284-133">application/vnd.ms-xpsdocument</span><span class="sxs-lookup"><span data-stu-id="af284-133">application/vnd.ms-xpsdocument</span></span>|

> [!NOTE]
> <span data-ttu-id="af284-134">Você não precisa registrar tipos MIME ou extensões de arquivo em sistemas cliente.</span><span class="sxs-lookup"><span data-stu-id="af284-134">You do not need to register MIME types or file extensions on client systems.</span></span> <span data-ttu-id="af284-135">Eles são registrados automaticamente quando você instala o Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="af284-135">They are registered automatically when you install Microsoft .NET Framework.</span></span>

<span data-ttu-id="af284-136">O exemplo a seguir do Microsoft Visual Basic Scripting Edition (VBScript) adiciona automaticamente os tipos MIME necessários ao IIS.</span><span class="sxs-lookup"><span data-stu-id="af284-136">The following Microsoft Visual Basic Scripting Edition (VBScript) sample automatically adds the necessary MIME types to IIS.</span></span> <span data-ttu-id="af284-137">Para usar o script, copie o código para um arquivo .vbs no seu servidor.</span><span class="sxs-lookup"><span data-stu-id="af284-137">To use the script, copy the code to a .vbs file on your server.</span></span> <span data-ttu-id="af284-138">Em seguida, execute o script executando o arquivo da linha de comando ou clicando duas vezes no arquivo no Microsoft Windows Explorer.</span><span class="sxs-lookup"><span data-stu-id="af284-138">Then, run the script by running the file from the command line or double-clicking the file in Microsoft Windows Explorer.</span></span>

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
> <span data-ttu-id="af284-139">A execução desse script várias vezes cria várias entradas de mapa MIME na metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="af284-139">Running this script multiple times creates multiple MIME map entries in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

<span data-ttu-id="af284-140">Depois de executar esse script, você não poderá ver tipos MIME adicionais do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0 Microsoft Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="af284-140">After you have run this script, you may not see additional MIME types from the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 Microsoft Management Console (MMC).</span></span> <span data-ttu-id="af284-141">No entanto, esses tipos MIME foram adicionados à metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="af284-141">However, these MIME types have been added to the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span> <span data-ttu-id="af284-142">O script a seguir exibirá todos os tipos de MIME na metabase do Microsoft Serviços de Informações da Internet (IIS) 5,0 ou do Microsoft Serviços de Informações da Internet (IIS) 6,0.</span><span class="sxs-lookup"><span data-stu-id="af284-142">The following script will display all the MIME types in the Microsoft Internet Information Services (IIS) 5.0 or Microsoft Internet Information Services (IIS) 6.0 metabase.</span></span>

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

<span data-ttu-id="af284-143">Salve o script como um arquivo `.vbs` (por exemplo, `DiscoverIISMimeTypes.vbs`) e execute-o no prompt de comando usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="af284-143">Save the script as a `.vbs` file (for example, `DiscoverIISMimeTypes.vbs`) and run it from the command prompt using the following command:</span></span>

```console
cscript DiscoverIISMimeTypes.vbs
```
