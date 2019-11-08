---
title: Pacote de fontes OpenType de amostra
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: a5b49e2a1f7536fb9d8e8f4dbfc53494dcd1f1ac
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740774"
---
# <a name="sample-opentype-font-pack"></a>Pacote de fontes OpenType de amostra
Este tópico fornece uma visão geral das fontes OpenType de exemplo que são distribuídas com o SDK do Windows. As fontes de exemplo dão suporte a recursos OpenType estendidos que podem ser usados por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos.  

<a name="overview"></a>   
## <a name="fonts-in-the-opentype-font-pack"></a>Fontes no pacote de fontes OpenType  
 O SDK do Windows fornece um conjunto de fontes OpenType de exemplo que você pode usar na criação de aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Essas fontes implementam apenas um subconjunto do total de recursos definidos pelo formato OpenType. A tabela a seguir lista os nomes das fontes OpenType de exemplo.  
  
|**Nome**|**Arquivo**|  
|--------------|--------------|  
|Kootenay|Kooten.ttf|  
|Lindsey|Linds.ttf|  
|Miramonte|Miramo.ttf|  
|Miramonte Bold|Miramob.ttf|  
|Pericles|Peric.ttf|  
|Pericles Light|Pericl.ttf|  
|Pescadero|Pesca.ttf|  
|Pescadero Bold|Pescab.ttf|  
  
 A ilustração a seguir mostra a aparência das fontes OpenType de exemplo.  
  
 ![Lista de nomes de fontes no pacote de fontes de exemplo](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Ascender é um provedor de produtos avançados de fontes. Para licenciar versões estendidas ou personalizadas das fontes de exemplo, consulte [Site de Web da Ascender Corporation](https://go.microsoft.com/fwlink/?LinkId=182627).  
  
> [!NOTE]
> Como desenvolvedor, é sua responsabilidade verificar se você tem os direitos de licença necessários de qualquer fonte inserida em um aplicativo ou redistribuída de outra forma.  
  
<a name="installing_the_fonts"></a>   
## <a name="installing-the-fonts"></a>Instalando as fontes  
 Você tem a opção de instalar as fontes OpenType de exemplo no diretório padrão de fontes do Windows, **\WINDOWS\Fonts**. Use o painel de controle Fontes para instalar as fontes. Depois que essas fontes estiverem em seu computador, elas poderão ser acessadas por todos os aplicativos que fazem referência às fontes padrão do Windows. Você pode exibir um conjunto representativo de caracteres em vários tamanhos de fonte clicando duas vezes no arquivo de fonte. A captura de tela a seguir mostra o arquivo de fonte Lindsey, Linds.tff.  
  
 ![Fonte Lindsey &#40;OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Exibindo a fonte Lindsey  
  
<a name="using_the_fonts"></a>   
## <a name="using-the-fonts"></a>Usando as fontes  
 Há duas maneiras de usar fontes no seu aplicativo. Você pode adicionar fontes ao seu aplicativo como itens de conteúdo de projeto que não são inseridos como recursos em um assembly. Como alternativa, você pode adicionar fontes ao seu aplicativo como itens de recurso de projeto que são inseridos nos arquivos de assembly do aplicativo. Para obter mais informações, consulte [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Documents.Typography>
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md)
