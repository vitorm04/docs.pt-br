---
title: Desenvolvimento entre plataformas com a Biblioteca de Classes Portátil
ms.date: 07/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 628c571ce645710482a29c813adb4fe1a59fd349
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43554630"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a>Desenvolvimento entre plataformas com a Biblioteca de Classes Portátil
O tipo de projeto de Biblioteca de Classes Portátil .NET Framework no Visual Studio ajuda a criar de maneira rápida e fácil aplicativos e bibliotecas de plataforma cruzada para plataformas Microsoft.  

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

 Bibliotecas de classes portáteis podem ajudar a reduzir o tempo e os custos com desenvolvimento e testes de código. Use esse tipo de projeto para gravar e criar assemblies .NET Framework portáteis e fazer referência a esses assemblies de aplicativos que tenham como destino várias plataformas, como Windows e Windows Phone.  
  
 Mesmo depois de criar um projeto de Biblioteca de Classes Portátil no Visual Studio e começar a desenvolvê-lo, é possível alterar as plataformas de destino. O Visual Studio compilará a biblioteca com os novos assemblies, o que ajuda a identificar as alterações necessárias ao código.  
  
 Este artigo discute o desenvolvimento de aplicativo no Visual Studio, mas a Microsoft também fornece assemblies de referência da Biblioteca de Classes Portátil que podem ser usados para desenvolver aplicativos e bibliotecas com outras ferramentas, como Xamarin. É possível usar esses aplicativos e bibliotecas em qualquer tempo de execução baseado em .NET Framework ou em plataformas que não sejam da Microsoft. Para obter mais informações sobre os assemblies de referência, consulte a entrada de blog [classe de biblioteca portátil (PCL) agora está disponível em todas as plataformas](https://blogs.msdn.com/b/dotnet/archive/2013/10/14/portable-class-library-pcl-now-available-on-all-platforms.aspx). Para baixar os assemblies, consulte [Assemblies de referência de biblioteca portátil do Microsoft .NET](https://www.microsoft.com/download/details.aspx?id=40727) no Microsoft Download Center. Para obter mais informações sobre como usar os assemblies com o Xamarin, consulte a entrada de blog [PCL e bibliotecas do .NET NuGet agora habilitadas para Xamarin](https://blogs.msdn.com/b/dotnet/archive/2013/11/13/pcl-and-net-nuget-libraries-are-now-enabled-for-xamarin.aspx).  
  
 O Visual Studio fornece modelos que ajudam a desenvolver com a Biblioteca de Classes Portátil. Dependendo da versão do Visual Studio que você está usando, os modelos e menus disponíveis podem ser diferentes dos descritos neste artigo.  
  
> [!WARNING]
>  Visual Studio 2013 atualização 2 inclui atualizações para os modelos de biblioteca de classes portátil. Se você tiver uma versão anterior do Visual Studio e Visual Studio 2013 instalado no mesmo computador e, em seguida, instalar a atualização 2, as alterações para o **estrutura de destino** opções serão aplicadas a ambas as versões do Visual Studio.  
  
 Neste tópico:  
  
 [Suporte do Visual Studio](#vs_support)  
 [Criando um projeto de biblioteca de classes portátil](#create_pcl)  
 [Opções de destino](#platforms)  
 [Alterando destinos](#change_targets)  
 [Recursos com suporte](#features)  
 [Os membros e tipos com suporte](#members)  
 [Diferenças de API na biblioteca de classes portátil](#API_diff)  
 [Usando a biblioteca de classes portátil](#using)  
  
<a name="vs_support"></a>   
## <a name="visual-studio-support"></a>Suporte a Visual Studio  
 O suporte a Visual Studio para a Biblioteca de Classes Portátil depende da versão do Visual Studio que você está usando. Em alguns casos, você terá tudo que precisa, enquanto em outros, precisará instalar itens adicionais, como mostra a tabela a seguir.  
  
|SKU do Visual Studio|Suporte para criação de uma Biblioteca de Classes Portátil|  
|-----------------------|---------------------------------------------------|  
|Visual Studio 2010, Professional, Premium ou Ultimate|Sim, quando você instala o [ferramentas de biblioteca portátil](https://marketplace.visualstudio.com/items?itemName=BCLTeam.PortableLibraryTools2).|  
|Versões do Visual Studio Express 2010|Não.|  
|Visual Studio 2012 Professional, Premium ou Ultimate|Sim. Para obter suporte do Windows Phone 8.0, instale o [Windows Phone SDK 8.0](https://www.microsoft.com/download/details.aspx?id=35471).|  
|Versões do Visual Studio Express 2012|Não.|  
|Visual Studio 2013 Professional, Premium ou Ultimate|Sim. Para obter suporte do Windows Phone 8.1, instale o [a versão mais recente do Visual Studio 2013](https://visualstudio.microsoft.com/vs/older-downloads/).|  
|Visual Studio Community 2013 para Windows|Sim, quando você instala o [a versão mais recente do Visual Studio Community 2013](https://visualstudio.microsoft.com/vs/older-downloads/), que inclui a atualização 2.|  
  
<a name="create_pcl"></a>   
## <a name="creating-a-portable-class-library-project"></a>Criando um projeto de Biblioteca de Classes Portátil  
 Para criar uma Biblioteca de Classes Portátil, use um dos modelos fornecidos no Visual Studio. Criar um novo projeto e, na **novo projeto** caixa de diálogo **modelos**, selecione o idioma de destino (c# ou Visual Basic) e, em seguida, selecione uma das plataformas de destino. É possível selecionar plataformas adicionais na próxima etapa.  
  
 No Visual Studio 2013 atualização 2, você pode escolher o **biblioteca de classes (portátil)** modelo para uma plataforma para criar uma biblioteca de classes portátil e o idioma escolhido. Você verá esse modelo para as seguintes plataformas:  
  
-   Aplicativos da Store  
  
-   Windows Desktop  
  
-   Silverlight  
  
 Se você quiser criar uma biblioteca de destino Windows Phone 8.1 e Windows 8.1 em c#, você poderá escolher **Store apps**e, em seguida, escolha **biblioteca de classes (portátil para aplicativos universais)**.  
  
 ![Biblioteca de classes portátil para aplicativos da Store](../../../docs/standard/cross-platform/media/storeuniversalpcl.png "StoreUniversalPCL")  
  
 Esse modelo seleciona automaticamente Windows 8.1 e Windows Phone 8.1 como destinos. Se você criar uma biblioteca que tenha como destino apenas Windows Phone 8.1 ou Windows 8.1, será possível alterar as plataformas de destino e adicionar plataformas mais tarde.  
  
 Se você estiver usando o Visual Studio 2012 ou Visual Studio 2013 sem a atualização 2, crie um novo projeto e escolha o **biblioteca de classes portátil** modelo no Visual c# ou Visual Basic.  
  
 ![Selecione o projeto de biblioteca portátil](../../../docs/standard/cross-platform/media/portablelibrary-start.png "PortableLibrary_start")  
  
 O **adicionar a biblioteca de classes portátil** caixa de diálogo é exibida e você pode selecionar plataformas adicionais. A caixa de diálogo exibe avisos de compatibilidade com base nos destinos selecionados.  
  
 ![Caixa de diálogo de estruturas de destino a alteração para VS2013](../../../docs/standard/cross-platform/media/clr-pcl-changeframeworks.png "CLR_PCL_ChangeFrameworks")  
Caixa de diálogo Adicionar Biblioteca de Classes Portátil para Visual Studio 2013 Atualização 2  
  
 Usando o Visual Studio 2012 ou o Visual Studio 2013, é possível selecionar as plataformas ao criar um projeto de Biblioteca de Classes Portátil ou usar as propriedades do projeto para modificar as plataformas de destino, depois da criação do projeto.  
  
<a name="platforms"></a>   
## <a name="target-options"></a>Opções de destino  
 Ao criar um projeto de Biblioteca de Classes Portátil, é possível escolher o sistema operacional e a versão do .NET Framework a serem usados como destino. Se você estiver usando o Visual Studio 2013 e tiver instalado a atualização 2 ou posterior, você pode escolher o **biblioteca de classes (portátil para aplicativos universais)** modelo para criar uma biblioteca de classes portátil que se destina ao Windows 8.1 e Windows Phone 8.1. A tabela a seguir mostra os destinos disponíveis dependendo da versão usada do Visual Studio.  
  
|Opções de destino|Visual Studio 2012|Visual Studio 2013|Visual Studio 2013 Atualização 2 ou posterior|  
|-|-|-|-|  
|.NET Framework|-.NET framework 4 e superior<br /><br /> -.NET framework 4.0.3 e superiores<br /><br /> -.NET framework 4.5|-.NET framework 4 e superior<br /><br /> -.NET framework 4.0.3 e superiores<br /><br /> -.NET framework 4.5 e superior<br /><br /> -.NET framework 4.5.1|-.NET framework 4<br /><br /> -.NET framework 4.0.3<br /><br /> -.NET framework 4.5<br /><br /> -.NET framework 4.5.1|  
|Windows Phone|-Windows Phone 7 e superior<br /><br /> -Windows Phone 7.5 e superior<br /><br /> -Windows Phone 8|-Windows Phone 8|-Windows Phone Silverlight 8<br /><br /> -Windows Phone Silverlight 8.1<br /><br /> No caso de suporte a Tempo de Execução do Windows e XAML, escolha:<br /><br /> -Windows Phone 8.1|  
|Windows Store|-.NET para aplicativos da Windows Store|-Windows Store Apps (Windows 8) e superior<br /><br /> -Aplicativos Windows Store (Windows 8.1)|-Windows 8<br /><br /> -Windows 8.1|  
|-O - Silverlight|-Silverlight 4 e superior<br /><br /> -Silverlight 5|-Silverlight 5|-Silverlight 5|  
|Xbox|-Xbox 360|N/D|N/D|  
  
<a name="change_targets"></a>   
## <a name="changing-targets"></a>Alterando destinos  
 Ao escolher um modelo de Biblioteca de Classes Portátil, são selecionadas as plataformas padrão para você, mas esses padrões variarão de acordo com a versão instalada do Visual Studio e dos destinos selecionados anteriormente. É possível alterar as plataformas ao criar a Biblioteca de Classes Portátil ou depois de iniciar o desenvolvimento de uma Biblioteca de Classes Portátil.  
  
 Se você quiser alterar os destinos depois de criar seu projeto, no **Gerenciador de soluções**, abra o menu de atalho para o seu projeto de biblioteca de classes portátil (não na solução) e, em seguida, escolha **propriedades** . Na página de propriedades de projeto, o **biblioteca** guia mostra as plataformas que o projeto está destinado atualmente.  
  
 ![Propriedades do projeto](../../../docs/standard/cross-platform/media/portablelibrary-projectproperties.png "PortableLibrary_ProjectProperties")  
Página de propriedade da Biblioteca de Classes Portátil para Visual Studio 2013 Atualização 2  
  
 Para adicionar ou remover destinos, escolha o **alteração** botão e, em seguida, selecione e desmarque as caixas de seleção apropriadas.  
  
 Ao alterar os destinos, as APIs disponíveis para desenvolver o projeto mudarão conforme a sua seleção. O Visual Studio relata os erros e avisos que podem ocorrer como resultado de alterações nos destinos.  
  
 Se você quiser avaliar a portabilidade de seus assemblies antes de fazer alterações no Visual Studio, você pode usar o [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).  
  
 As opções de menu variarão de acordo com a versão do Visual Studio em uso.  
  
 ![Alterar destino](../../../docs/standard/cross-platform/media/portablelibrary.png "PortableLibrary_")  
Caixa de diálogo Alterar Destinos no Visual Studio 2012  
  
<a name="features"></a>   
## <a name="supported-features"></a>Recursos com suporte  
 A tabela a seguir mostra quais recursos são suportados nas plataformas e versões disponíveis. Em alguns casos, a Microsoft adicionou suporte com a liberação de um pacote NuGet, e isso foi notado. Para obter mais informações sobre pacotes do NuGet para o .NET Framework, consulte [o .NET Framework e lançamentos fora de banda](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
|Recurso|.NET Framework|.NET Framework|.NET Framework|Windows Store|Windows Store|Windows Phone Store|Windows Phone Silverlight|Windows Phone Silverlight|Windows Phone Silverlight|Silverlight|Silverlight|Xbox 360|  
|-------------|--------------------|--------------------|--------------------|-------------------|-------------------|-------------------------|-------------------------------|-------------------------------|-------------------------------|-----------------|-----------------|--------------|  
||**4**|**4.0.3**|**4.5**|**8**|**8.1**|**8.1**|**7.5**|**8**|**8.1**|**4**|**5**||  
|Bibliotecas principais|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
|Suporte assíncrono|➊|➊|✓|✓|✓|✓|➊|➊|✓|➊|➊||  
|Compactação|||✓|✓|✓|✓||➋|➋||||  
|Anotações de dados||✓|✓|✓|✓|||||✓|✓||  
|Palavra-chave dinâmica|✓|✓|✓|✓|✓|||||✓|✓||  
|HTTPClient|➌|➌|✓|✓|✓|✓|➌|➌|➌|➌|➌||  
|IQueryable|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|LINQ (Consulta Integrada à Linguagem)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|MEF (Managed Extensibility Framework)|✓|✓|✓|✓|✓|||||✓|✓||  
|NCL (Network Class Library)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Serialização (contrato de dados, XML e JSON)|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|System.Numerics|✓|✓|✓|✓|✓|||||✓|✓||  
|Modelos de visualização (MVVM)|||✓|✓|✓|✓|✓|✓|✓|✓|✓||  
|Windows Communication Foundation (WCF)|✓|✓|✓|✓|✓||✓|✓|✓|✓|✓||  
|APIs do Tempo de Execução do Windows|||||✓|✓|||||||  
|Windows.UI.XAML|||||✓|✓|||||||  
|XLINQ||✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|✓|  
  
 Requer ➊ [Microsoft Async](https://www.nuget.org/packages/Microsoft.Bcl.Async/) pacote  
 Requer ➋ [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) pacote  
 Requer ➌ [bibliotecas de cliente HTTP Microsoft](https://www.nuget.org/packages/Microsoft.Net.Http) pacote  
  
> [!WARNING]
>  Você pode encontrar erros ao fazer referência a [Microsoft Compression](https://www.nuget.org/packages/Microsoft.Bcl.Compression) e [Microsoft HTTP Client Libraries](https://www.nuget.org/packages/Microsoft.Net.Http) pacotes a partir de uma biblioteca portátil usada por um aplicativo do Windows Phone Silverlight 8.1. Para obter mais informações, consulte [compatibilidade de plataforma e alterações interruptivas para aplicativos Windows Phone Silverlight 8.1](https://docs.microsoft.com/previous-versions/windows/apps/dn642084(v=vs.105)).  
  
<a name="members"></a>   
## <a name="supported-types-and-members"></a>Tipos e membros com suporte  
 Os tipos e membros disponíveis em projetos da Biblioteca de Classes Portátil são restritos por vários fatores de compatibilidade:  
  
-   Eles devem ser compartilhados entre os destinos selecionados.  
  
-   Eles devem se comportar de forma semelhante nesses destinos.  
  
-   Eles não devem ser candidatos à substituição.  
  
-   Eles devem fazer sentido em um ambiente portátil, especialmente quando os membros de suporte não são portáveis.  
  
 Por exemplo, a Biblioteca de Classes Portátil contém tipos relacionados a interface de usuário apenas quando os destinos são Windows 8.1 e Windows Phone 8.1. Além disso, você também pode encontrar limitações se usar plataformas de destino (como Xbox, .NET Framework 4 e Windows Phone 7) que foram lançadas antes da introdução da Biblioteca de Classes Portátil. O .NET Framework libera pacotes através do NuGet que aprimoram o suporte da Biblioteca de Classes Portátil para algumas dessas plataformas mais antigas. Para obter mais informações e uma lista de pacotes do NuGet, consulte [o .NET Framework e lançamentos fora de banda](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md).  
  
 Se houver suporte a um membro na Biblioteca de Classes Portátil e aos destinos selecionados, isso aparecerá no projeto no IntelliSense. Além disso, o ícone da biblioteca de classes portátil ![com suporte pela biblioteca portátil](../../../docs/standard/cross-platform/media/portablelibrary-referenceicon.png "PortableLibrary_ReferenceIcon") é exibida em tabelas de membros, o [biblioteca de classes do .NET Framework](https://msdn.microsoft.com/library/mt472912.aspx) Avançar para membros com suporte. Por exemplo, a tabela de membros a seguir mostra que a propriedade <xref:System.String.Chars%2A> na classe <xref:System.String> tem suporte na Biblioteca de Classes Portátil:  
  
 ![Ícone do membro com suporte](../../../docs/standard/cross-platform/media/plibsupportedmemberlist.png "PlibSupportedMemberList")  
Ícone da Biblioteca de classes portátil  
  
 Você também pode examinar a **informações de versão** seção de um tópico de referência para uma nota indicando que um tipo ou membro tem suporte no projeto de biblioteca de classes portátil:  
  
 ![Informações de versão da biblioteca portátil](../../../docs/standard/cross-platform/media/plibversioninformation.png "PlibVersionInformation")  
Exemplo de informações de versão  
  
 Porém, lembre-se de que uma API pode ter suporte na Biblioteca de Classes Portátil, mas sua capacidade de usá-la dependerá dos destinos selecionados.  
  
<a name="API_diff"></a>   
## <a name="api-differences-in-the-portable-class-library"></a>Diferenças de API na Biblioteca de Classes Portátil  
 Para tornar os assemblies da Biblioteca de Classes Portátil compatíveis entre todas as plataformas com suporte, alguns membros foram ligeiramente alterados na Biblioteca de Classes Portátil.  
  
<a name="using"></a>   
## <a name="using-the-portable-class-library"></a>Usando a Biblioteca de Classes Portátil  
 Depois de criar o projeto da Biblioteca de Classes Portátil, você simplesmente faz uma referência a ele em outros projetos. Você pode fazer referência ao projeto ou assemblies específicos que contêm as classes que deseja acessar.  
  
 Para executar um aplicativo que faça referência a um assembly da Biblioteca de Classes Portátil, deve ser instalada a versão necessária (ou uma versão posterior) das plataformas de destino no computador. O Visual Studio contém todas as estruturas necessárias, assim, você pode executar aplicativos sem alteração adicional no computador usado para desenvolver o aplicativo.  
  
### <a name="deploying-a-windows-store-or-windows-phone-app"></a>Implantando um aplicativo da Windows Store ou do Windows Phone  
 Ao criar um aplicativo da Windows Store ou do Windows Phone que faça referência a um assembly da Biblioteca de Classes Portátil, tudo o que é necessário para implantar o aplicativo está incluído no pacote do aplicativo e mais nenhuma etapa é necessária.  
  
### <a name="deploying-a-net-framework-app"></a>Implantando um aplicativo do .NET Framework  
 Ao implantar o aplicativo do .NET Framework que faça referência a um assembly da Biblioteca de Classes Portátil, você deve especificar uma dependência na versão correta do .NET Framework. Ao especificar essa dependência, você garante que a versão requisitada seja instalada com seu aplicativo. Se você direcionar o .NET Framework 4 ou posterior, o computador deve ter o .NET Framework 4 com uma [atualizar](https://www.microsoft.com/download/details.aspx?id=3556), atualização 4.0.3 para o .NET Framework 4 ou .NET Framework 4.5 instalado.  
  
-   Para criar uma dependência com a implantação do ClickOnce: no **Gerenciador de soluções**, escolha o nó do projeto para o projeto que você deseja publicar. (Esse projeto faz referência ao projeto da Biblioteca de Classes Portátil.) Na barra de menus, escolha **Project**, **Properties**e, em seguida, escolha o **publicar** guia. Sobre o **Publish** , escolha **pré-requisitos**. Selecione a versão necessária do .NET Framework (ou a atualização do .NET Framework 4) como um pré-requisito.  
  
-   Para criar uma dependência com um projeto de instalação: nos **Gerenciador de soluções**, escolha o projeto de instalação. Na barra de menus, escolha **Project**, **Properties**, **pré-requisitos**. Selecione a versão necessária do .NET Framework como um pré-requisito.  
  
 Para obter mais informações sobre como implantar aplicativos do .NET Framework, consulte [guia de implantação para os desenvolvedores](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
### <a name="deploying-a-silverlight-based-app"></a>Implantando um aplicativo com base no Silverlight  
 Ao implantar um aplicativo com base no Silverlight que referencia um assembly da Biblioteca de Classes Portátil, você deve garantir que a versão do tempo de execução mínima necessária para o aplicativo corresponda à sua versão de destino. Se seu destino é o Silverlight 4, a versão deve ser a 4.0.60129.0 ou posterior. Você define a versão ao incluir `<param name="minRuntimeVersion" value="4.0.60129.0" />` na página da Web que hospeda o aplicativo baseado em Silverlight da seguinte forma:  
  
```xaml  
<div id="silverlightControlHost">  
    <object data="data:application/x-silverlight-2,"   
           type="application/x-silverlight-2" width="100%" height="100%">  
    <param name="source" value="ClientBin/SilverlightApplication.xap"/>  
    <param name="onError" value="onSilverlightError" />  
    <param name="background" value="white" />  
    <param name="minRuntimeVersion" value="4.0.60129.0" />  
    <param name="autoUpgrade" value="true" />  
    <a href="https://www.microsoft.com/getsilverlight/get-started/install/"   
             style="text-decoration:none">  
      <img src=http://download.microsoft.com/download/5/1/6/5165823D-1D79-4871-8AC2-42DDDB94A5C2/PNGs/SLMedallion_ENU.png  
             alt="Get Microsoft Silverlight" style="border-style:none"/>  
    </a>  
  </object>  
   <iframe id="_sl_historyFrame"   
              style="visibility:hidden;height:0px;width:0px;border:0px">  
   </iframe>  
</div>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Usando a biblioteca de classes portátil com modelo MVVM](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)  
 [Recursos do aplicativo para bibliotecas direcionadas a várias plataformas](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)  
 [.NET portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b)  
 [Suporte do .NET Framework para Aplicativos da Windows Store e Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [Implantação](../../../docs/framework/deployment/net-framework-applications.md)
