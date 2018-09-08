---
title: Exemplo de tecnologia de serialização genérica de serviços Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: b233ed4374231c7e7ff2b6617a63c4e4c94612c2
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177864"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Exemplo de tecnologia de serialização genérica de serviços Web
[Baixar Exemplo](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Esse exemplo mostra como usar e controlar a serialização de genéricos em Serviços Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1.  Abra o Visual Studio e selecione **Novo Site** no menu **Arquivo**.  
  
2.  Na caixa de diálogo **Novo Site**, selecione no painel esquerdo a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.  
  
3.  Clique em **Procurar** e navegue para o subdiretório \CS\GenericsService.  
  
4.  Selecione Service.asmx para abrir o arquivo no Visual Studio.  
  
5.  No menu **Compilar**, clique em **Compilar Solução**.  
  
> [!NOTE]
>  As primeiras cinco etapas nessa lista são opcionais. O tempo de execução do .NET Framework automaticamente gerarão o serviço Web da primeira vez que o serviço for solicitado.  
  
> [!NOTE]
>  As seguintes etapas são necessárias para criar o exemplo.  
  
1.  Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue até o subdiretório \CS.  
  
2.  Clique com o botão direito do mouse no ícone do subdiretório GenericsService e selecione **Compartilhamento e Segurança**.  
  
3.  Na guia **Compartilhamento da Web**, selecione **Compartilhar esta Pasta**.  
  
> [!IMPORTANT]
>  Anote o nome do diretório virtual listado no painel **Aliases**, pois você precisará dele para executar a amostra.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Para criar o exemplo usando os Serviços de Informações da Internet  
  
1.  Abra o snap-in de gerenciamento **Serviços de Informações da Internet** e expanda **Sites**.  
  
2.  Clique com o botão esquerdo do mouse em **Site Padrão**, selecione **Novo** e, em seguida, selecione **Diretório Virtual?** para criar o **Assistente de Criação de Diretório Virtual**.  
  
3.  Clique em **Avançar**, insira o alias público do diretório virtual e clique em **Avançar**.  
  
4.  Insira o caminho para o diretório no qual você salvou a amostra (normalmente o subdiretório \CS\GenericsService) e clique em **Avançar**. Clique em **Avançar** para concluir o assistente.  
  
> [!IMPORTANT]
>  Anote o nome do diretório virtual listado no painel **Alias**, pois você precisará dele para executar a amostra.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra uma janela do navegador e selecione sua barra de endereços.  
  
2.  Tipo de `http://localhost/[virtual directory]/Service.asmx`, onde `[virtual directory]` representa o diretório virtual que você criou ao criar o exemplo.  
  
## <a name="remarks"></a>Comentários  
 O exemplo exibe uma página ASP.NET padrão que contém links para a definição do Serviço Web. Você pode personalizar a exibição além de modificar o código de origem para o serviço Web. Para obter mais informações, consulte [Criando clientes de serviço Web XML](https://msdn.microsoft.com/library/c606f3cb-4111-45b4-ae42-9300420fa16c).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>  
- <xref:System.Web.Services>  
- <xref:System.Xml.Serialization>  
- [Serialização](../../../docs/standard/serialization/index.md)  
- [Serviços Web XML criados com o ASP.NET e clientes de serviços Web XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)
