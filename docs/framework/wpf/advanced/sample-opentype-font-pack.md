---
title: Pacote de fontes OpenType de amostra
ms.date: 03/30/2017
helpviewer_keywords:
- OpenType font pack [WPF]
- fonts [WPF], OpenType font pack
- typography [WPF], OpenType font pack
ms.assetid: 56b46fa1-a44e-419b-8f14-25ad51c715c3
ms.openlocfilehash: 30cb69fcf05108822e8f3e2d45c9e79dbced26ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181907"
---
# <a name="sample-opentype-font-pack"></a>Pacote de fontes OpenType de amostra
Este tópico fornece uma visão geral das fontes OpenType de exemplo distribuídas com o SDK do Windows. As fontes de exemplo suportam recursos opentype estendidos que podem ser usados por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos.  

<a name="overview"></a>
## <a name="fonts-in-the-opentype-font-pack"></a>Fontes no pacote de fontes OpenType  
 O Windows SDK fornece um conjunto de fontes OpenType [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de exemplo que você pode usar na criação de aplicativos. As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Essas fontes implementam apenas um subconjunto dos recursos totais definidos pelo formato OpenType. A tabela a seguir lista os nomes das fontes OpenType de exemplo.  
  
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
  
 A ilustração a seguir mostra como são as fontes OpenType da amostra.  
  
 ![Lista de nomes de fontes no pacote de fontes de exemplo](./media/sample-opentype-font-pack/font-names-sample-pack.gif)  
  
 As fontes de exemplo são fornecidas sob licença da Ascender Corporation. Ascender é um provedor de produtos avançados de fontes. Para licenciar versões estendidas ou personalizadas das fontes de exemplo, consulte [Site de Web da Ascender Corporation](https://www.monotype.com/).  
  
> [!NOTE]
> Como desenvolvedor, é sua responsabilidade verificar se você tem os direitos de licença necessários de qualquer fonte inserida em um aplicativo ou redistribuída de outra forma.  
  
<a name="installing_the_fonts"></a>
## <a name="installing-the-fonts"></a>Instalando as fontes  
 Você tem a opção de instalar as fontes OpenType de amostra no diretório padrão do Windows Fonts, **\WINDOWS\Fonts**. Use o painel de controle Fontes para instalar as fontes. Uma vez que essas fontes estejam no seu computador, elas estão acessíveis a todos os aplicativos que fazem referência a fontes padrão do Windows. Você pode exibir um conjunto representativo de caracteres em vários tamanhos de fonte clicando duas vezes no arquivo de fonte. A captura de tela a seguir mostra o arquivo de fonte Lindsey, Linds.tff.  
  
 ![Fonte Lindsey &#40;OpenType&#41;](./media/typographyinwpf-04.png "TypographyInWPF_04")  
Exibindo a fonte Lindsey  
  
<a name="using_the_fonts"></a>
## <a name="using-the-fonts"></a>Usando as fontes  
 Há duas maneiras de usar fontes no seu aplicativo. Você pode adicionar fontes ao seu aplicativo como itens de conteúdo de projeto que não são inseridos como recursos em um assembly. Como alternativa, você pode adicionar fontes ao seu aplicativo como itens de recurso de projeto que são inseridos nos arquivos de assembly do aplicativo. Para obter mais informações, consulte [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md).  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Documents.Typography>
- [Recursos de fonte OpenType](opentype-font-features.md)
- [Empacotando fontes com aplicativos](packaging-fonts-with-applications.md)
