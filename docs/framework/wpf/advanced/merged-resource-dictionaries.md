---
title: Dicionários de recursos mesclados
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 466a18a58acfebf6d779a1d0eba3d2637743806e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911720"
---
# <a name="merged-resource-dictionaries"></a>Dicionários de recursos mesclados
Os recursos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dão suporte a um recurso de dicionário de recursos mesclados. Esse recurso fornece uma maneira de definir a parte de recursos de um aplicativo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fora do aplicativo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilado. Os recursos podem ser compartilhados entre aplicativos e são também isolados de modo mais conveniente para localização.  
  
## <a name="introducing-a-merged-resource-dictionary"></a>Apresentando um dicionário de recursos mesclados  
 Na marcação, você pode usar a seguinte sintaxe para introduzir um dicionário de recursos mesclados em uma página:  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 Observe que o <xref:System.Windows.ResourceDictionary> elemento não tem uma [diretiva x:Key](../../xaml-services/x-key-directive.md), que geralmente é necessária para todos os itens em uma coleção de recursos. Mas outra <xref:System.Windows.ResourceDictionary> referência dentro da <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> coleção é um caso especial, reservada para esse cenário de dicionário de Recursos mesclados. O <xref:System.Windows.ResourceDictionary> que introduz um dicionário de Recursos mesclados não pode ter uma [diretiva x:Key](../../xaml-services/x-key-directive.md). Normalmente, cada <xref:System.Windows.ResourceDictionary> uma dentro <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> da coleção especifica <xref:System.Windows.ResourceDictionary.Source%2A> um atributo. O valor de <xref:System.Windows.ResourceDictionary.Source%2A> deve ser um [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] que seja resolvido para o local do arquivo de recursos a ser mesclado. O destino de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] deve ser outro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo, com <xref:System.Windows.ResourceDictionary> como seu elemento raiz.  
  
> [!NOTE]
> É válido definir recursos dentro de um <xref:System.Windows.ResourceDictionary> que é especificado como um dicionário mesclado, como uma alternativa para especificar <xref:System.Windows.ResourceDictionary.Source%2A>ou além de quaisquer recursos incluídos da origem especificada. No entanto, esse não é um cenário comum. O cenário principal para dicionários mesclados é mesclar recursos de locais de arquivo externo. Se você quiser especificar recursos dentro da marcação de uma página, normalmente você deve defini-los no principal <xref:System.Windows.ResourceDictionary> e não nos dicionários mesclados.  
  
## <a name="merged-dictionary-behavior"></a>Comportamento do dicionário mesclado  
 Os recursos em um dicionário mesclado ocupam um local no escopo de pesquisa de recurso que está logo após o escopo do dicionário de recursos principal no qual eles são mesclados. Embora uma chave de recurso deva ser exclusiva em qualquer dicionário individual, uma chave pode existir várias vezes em um conjunto de dicionários mesclados. Nesse caso, o recurso retornado será proveniente do último dicionário encontrado sequencialmente na <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> coleção. Se a <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> coleção tiver sido definida [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]em, a ordem dos dicionários mesclados na coleção será a ordem dos elementos conforme fornecido na marcação. Se uma chave for definida no dicionário principal e também em um dicionário que foi mesclado, o recurso que será retornado virá do dicionário principal. Essas regras de escopo se aplicam igualmente para referências de recursos estáticos e referências de recursos dinâmicos.  
  
### <a name="merged-dictionaries-and-code"></a>Dicionários mesclados e código  
 Os dicionários mesclados podem ser adicionados a um dicionário `Resources` por meio do código. O padrão, inicialmente vazio <xref:System.Windows.ResourceDictionary> , que existe para `Resources` qualquer propriedade também tem uma propriedade de coleção <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> padrão, inicialmente vazia. Para adicionar um dicionário mesclado por meio de código, você obtém uma referência para o <xref:System.Windows.ResourceDictionary>primário desejado, <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> obtém seu valor de propriedade `Add` e chama o `Collection` genérico que está contido <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>em. O objeto que você adicionar deve ser um <xref:System.Windows.ResourceDictionary>novo. No código, você não define a <xref:System.Windows.ResourceDictionary.Source%2A> propriedade. Em vez disso, você deve <xref:System.Windows.ResourceDictionary> obter um objeto criando um ou carregando um. Uma maneira de carregar um existente <xref:System.Windows.ResourceDictionary> para chamar <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> em um fluxo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de arquivos existente que tem <xref:System.Windows.ResourceDictionary> uma raiz e, em <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> seguida, converter <xref:System.Windows.ResourceDictionary>o valor de retorno para.  
  
### <a name="merged-resource-dictionary-uris"></a>URIs de dicionários de recursos mesclados  
 Há várias técnicas para saber como incluir um dicionário de recursos mesclados, que são indicadas pelo formato [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] que será usado. Genericamente, essas técnicas podem ser divididas em duas categorias: recursos que são compilados como parte do projeto e recursos que não são compilados como parte do projeto.  
  
 Para obter recursos que são compilados como parte do projeto, você pode usar um caminho relativo que se refere ao local do recurso. O caminho relativo é avaliado durante a compilação. O recurso deve ser definido como parte do projeto como uma ação de build de recursos. Se incluir um arquivo .xaml de recurso no projeto como recurso, você não precisará copiar o arquivo de recurso no diretório de saída, pois o recurso já estará incluído no aplicativo compilado. Você também pode usar a ação de build de conteúdo, mas deve, em seguida, copiar os arquivos no diretório de saída e também implantar os arquivos de recursos na mesma relação de caminho para o executável.  
  
> [!NOTE]
> Não use a ação de build do recurso inserido. A própria ação de compilação tem suporte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para aplicativos, mas a resolução <xref:System.Windows.ResourceDictionary.Source%2A> de não é <xref:System.Resources.ResourceManager>incorporada e, portanto, não pode separar o recurso individual do fluxo. Você ainda pode usar o recurso incorporado para outras finalidades, desde que você <xref:System.Resources.ResourceManager> também tenha usado para acessar os recursos.  
  
 Uma técnica relacionada é usar um URI Pack para um arquivo [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e fazer referência a ele como fonte. O URI Pack permite referências a componentes de assemblies referenciados e outras técnicas. Para mais informações sobre URIs Pack, consulte [Arquivos de recurso, conteúdo e dados do aplicativo WPF](../app-development/wpf-application-resource-content-and-data-files.md).  
  
 Para obter recursos que não são compilados como parte do projeto, o URI é avaliado no tempo de execução. Você pode usar um transporte comum de URI como arquivo: ou http: para fazer referência ao arquivo de recursos. A desvantagem de usar a abordagem de recursos não compilados é que o acesso ao arquivo: requer etapas adicionais de implantação e o acesso ao http: implica na zona de segurança da Internet.  
  
### <a name="reusing-merged-dictionaries"></a>Reutilizando dicionários mesclados  
 Você pode reutilizar ou compartilhar dicionários de recursos mesclados entre aplicativos, pois o dicionário de recursos a ser mesclado pode ser referenciado por meio de qualquer [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] válido. O modo exato de fazer isso depende de sua estratégia de implantação do aplicativo e qual modelo de aplicativo você segue. A estratégia do URI Pack mencionado fornece uma maneira comum de prover um recurso mesclado em vários projetos durante o desenvolvimento ao compartilhar uma referência de assembly. Nesse cenário, os recursos ainda são distribuídos pelo cliente e pelo menos um dos aplicativos deve implantar o assembly referenciado. Também é possível referenciar recursos mesclados pelo URI distribuído que usa o protocolo http.  
  
 Gravar dicionários mesclados como arquivos de aplicativo local ou para armazenamento local compartilhado é outro cenário de dicionário mesclado/implantação do aplicativo possível.  
  
### <a name="localization"></a>Localização  
 Se recursos que precisam ser localizados estiverem isolados para os dicionários que são mesclados em dicionários principais e mantidos como [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] flexível, esses arquivos poderão ser localizados separadamente. Essa técnica é uma alternativa simples para localizar os assemblies satélite de recursos. Para detalhes, consulte [Visão geral de globalização e localização do WPF](wpf-globalization-and-localization-overview.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.ResourceDictionary>
- [Recursos XAML](xaml-resources.md)
- [Recursos e código](resources-and-code.md)
- [Arquivos de recursos, de conteúdo e de dados de aplicativos do WPF](../app-development/wpf-application-resource-content-and-data-files.md)
