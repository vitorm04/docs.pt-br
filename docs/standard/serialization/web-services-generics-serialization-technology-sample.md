---
title: Exemplo de tecnologia de serialização genérica de serviços Web
ms.date: 03/30/2017
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
ms.openlocfilehash: 6549dc1c3d428a5fb74fe0212549ef3f3f6510d1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299651"
---
# <a name="web-services-generics-serialization-technology-sample"></a>Exemplo de tecnologia de serialização genérica de serviços Web
[Baixar exemplo](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 Esse exemplo mostra como usar e controlar a serialização de genéricos em Serviços Web ASP.NET.  
  
### <a name="to-build-the-sample-using-visual-studio"></a>Para criar o exemplo usando Visual Studio  
  
1. Abra o Visual Studio e selecione **Novo Site** no menu **Arquivo**.  
  
2. Na caixa de diálogo **Novo Site**, selecione no painel esquerdo a linguagem de programação desejada e, em seguida, no painel esquerdo, selecione **Serviço Web ASP.NET**.  
  
3. Clique em **Procurar** e navegue para o subdiretório \CS\GenericsService.  
  
4. Selecione Service.asmx para abrir o arquivo no Visual Studio.  
  
5. No menu **Compilar**, clique em **Compilar Solução**.  
  
> [!NOTE]
>  As primeiras cinco etapas nessa lista são opcionais. O tempo de execução do .NET Framework automaticamente gerarão o serviço Web da primeira vez que o serviço for solicitado.  
  
> [!NOTE]
>  As seguintes etapas são necessárias para criar o exemplo.  
  
1. Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue até o subdiretório \CS.  
  
2. Clique com o botão direito do mouse no ícone do subdiretório GenericsService e selecione **Compartilhamento e Segurança**.  
  
3. Na guia **Compartilhamento da Web**, selecione **Compartilhar esta Pasta**.  
  
> [!IMPORTANT]
>  Anote o nome do diretório virtual listado no painel **Aliases**, pois você precisará dele para executar a amostra.  
  
### <a name="to-build-the-sample-using-internet-information-services"></a>Para criar o exemplo usando os Serviços de Informações da Internet  
  
1. Abra o snap-in de gerenciamento **Serviços de Informações da Internet** e expanda **Sites**.  
  
2. Clique com o botão esquerdo do mouse em **Site Padrão**, selecione **Novo** e, em seguida, selecione **Diretório Virtual?** para criar o **Assistente de Criação de Diretório Virtual**.  
  
3. Clique em **Avançar**, insira o alias público do diretório virtual e clique em **Avançar**.  
  
4. Insira o caminho para o diretório no qual você salvou a amostra (normalmente o subdiretório \CS\GenericsService) e clique em **Avançar**. Clique em **Avançar** para concluir o assistente.  
  
> [!IMPORTANT]
>  Anote o nome do diretório virtual listado no painel **Alias**, pois você precisará dele para executar a amostra.  
  
### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra uma janela do navegador e selecione sua barra de endereços.  
  
2. Tipo de `http://localhost/[virtual directory]/Service.asmx`, onde `[virtual directory]` representa o diretório virtual que você criou ao criar o exemplo.  
  
## <a name="remarks"></a>Comentários  
 O exemplo exibe uma página ASP.NET padrão que contém links para a definição do Serviço Web. Você pode personalizar a exibição além de modificar o código de origem para o serviço Web. Para obter mais informações, consulte [Criando clientes de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w3h45ebk(v=vs.100)).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- <xref:System.Web.Services>
- <xref:System.Xml.Serialization>
- [Serialização](../../../docs/standard/serialization/index.md)
- [Serviços Web XML criados usando ASP.NET e clientes de serviço Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))
