---
title: Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web
ms.date: 03/30/2017
helpviewer_keywords:
- debugging XBAPs that call a Web service [WPF]
- debugging security exceptions for XBAPs [WPF]
- security exception for XBAPs [WPF], debugging
- configuring Visual Studio to debug XAML browser applications [WPF]
- configuring Visual Studio to debug XBAPs [WPF]
ms.assetid: fd1db082-a7bb-4c4b-9331-6ad74a0682d0
ms.openlocfilehash: d8cfae2fb47876d578c51e5f4acdfe0c31e752fe
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460908"
---
# <a name="how-to-configure-visual-studio-to-debug-a-xaml-browser-application-to-call-a-web-service"></a>Como configurar o Visual Studio para depurar um aplicativo de navegador XAML para chamar um serviço Web
Os aplicativos de navegador XAML (XBAPs) são executados em uma área de segurança de confiança parcial que é restrita ao conjunto de permissões de zona da Internet. Esse conjunto de permissões restringe as chamadas de serviço Web somente a serviços Web que estão localizados no site de origem do aplicativo XBAP. No entanto, quando um XBAP é depurado do Visual Studio 2005, não é considerado ter o mesmo site de origem que o serviço Web referenciado. Isso faz com que as exceções de segurança sejam geradas quando o XBAP tentar chamar o serviço Web. No entanto, um projeto do WPF (aplicativo de navegador XAML) do Visual Studio 2005 pode ser configurado para simular ter o mesmo site de origem que o serviço Web que ele chama durante a depuração. Isso permite que o XBAP chame com segurança o serviço Web sem causar exceções de segurança.

## <a name="configuring-visual-studio"></a>Configurando o Visual Studio
 Para configurar o Visual Studio 2005 para depurar um XBAP que chama um serviço Web:

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. No **Designer de Projeto**, clique na guia **Depurar**.

3. Na seção **Iniciar Ação**, selecione **Iniciar programa externo** e insira o seguinte:

     `C:\WINDOWS\System32\PresentationHost.exe`

4. Na seção **Opções de inicialização**, digite o seguinte na caixa de texto **Argumentos da linha de comando**:

     *nome de arquivo* `-debug`

     O valor *filename* para o parâmetro **-debug** é o nome do arquivo .xbap; por exemplo:

     `-debug c:\example.xbap`

> [!NOTE]
> Essa é a configuração padrão para soluções que são criadas com o modelo de projeto do WPF (aplicativo de navegador XAML) do Visual Studio 2005.

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. No **Designer de Projeto**, clique na guia **Depurar**.

3. Na seção **Opções de inicialização**, adicione o seguinte parâmetro de linha de comando para a caixa de texto **Argumentos de linha de comando**:

     `-debugSecurityZoneURL`  *URL*

     O valor da *URL* para o parâmetro **-DEBUGSECURITYZONEURL** é a URL para o local que você deseja simular como sendo o site de origem do seu aplicativo.

 Como exemplo, considere um aplicativo de navegador XAML (XBAP) que usa um serviço Web com a seguinte URL:

 `http://services.msdn.microsoft.com/ContentServices/ContentService.asmx`

 A URL do site de origem para este serviço Web é:

 `http://services.msdn.microsoft.com`

 Consequentemente, o parâmetro de linha de comando completo **-debugSecurityZoneURL** e seu valor é:

 `-debugSecurityZoneURL http://services.msdn.microsoft.com`

## <a name="see-also"></a>Consulte também

- [Host do WPF (PresentationHost.exe)](wpf-host-presentationhost-exe.md)
