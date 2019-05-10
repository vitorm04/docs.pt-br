---
title: Atributos de localização e comentários
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: a242dc1f69c79b2c1a67c1a9235d3e942553caf1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598737"
---
# <a name="localization-attributes-and-comments"></a>Atributos de localização e comentários
Os comentários de localização de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] são propriedades, dentro do código-fonte [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], fornecidas pelos desenvolvedores para conceder as regras e dar dicas de localização. Os comentários de localização de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] contêm dois conjuntos de informações: atributos de possibilidade de localização e comentários de localização de forma livre. Os atributos de possibilidade de localização são usados pela API de localização [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] para indicar quais recursos devem ser localizados. Os comentários de forma livre são todas as informações que o criador do aplicativo desejar incluir.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Comentários de localização  
 Se os autores do aplicativo de marcação tiverem requisitos de elementos específicos em [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)], como as restrições no comprimento do texto, a família de fontes ou o tamanho da fonte, eles poderão transmitir essas informações aos localizadores com comentários no código [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. O processo para adicionar comentários ao código-fonte é o seguinte:  
  
1. O desenvolvedor de aplicativos adiciona comentários de localização no código-fonte [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
2. Durante o processo de build, você pode especificar no arquivo .proj se deixa os comentários de localização de forma livre no assembly, remove parte dos comentários ou todos os comentários. Os comentários removidos são colocados em um arquivo separado. Você especifica sua opção usando uma marca `LocalizationDirectivesToLocFile`, por exemplo:  
  
     `<LocalizationDirectivesToLocFile>`*valor*`</LocalizationDirectivesToLocFile>`  
  
3. Os valores que podem ser atribuídos são:  
  
    - **None** – os comentários e atributos permanecem dentro do assembly e nenhum arquivo separado é gerado.  
  
    - **CommentsOnly** – remove somente os comentários do assembly e os coloca em um LocFile separado.  
  
    - **All** – remove os comentários e os atributos do assembly e os coloca em um LocFile separado.  
  
4. Quando os recursos localizáveis são extraídos do [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)], os atributos de possibilidade de localização são respeitados pela API de localização [!INCLUDE[TLA2#tla_baml](../../../../includes/tla2sharptla-baml-md.md)].  
  
5. Os arquivos de comentário de localização, que contém apenas comentários de forma livre, são incorporados ao processo de localização em um momento posterior.  
  
 O exemplo a seguir mostra como adicionar comentários de localização em um arquivo [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)].  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 No exemplo anterior, a seção Localization.Attributes contém os atributos de localização e a seção Localization.Comments contém os comentários de forma livre. As tabelas a seguir mostram os atributos e comentários e seu significado para o localizador.  
  
|Atributos de localização|Significado|  
|-----------------------------|-------------|  
|$Content (texto legível não modificável)|O conteúdo do elemento TextBlock não pode ser modificado. Os localizadores não podem alterar a palavra "Microsoft". O conteúdo é visível (legível) para o localizador. A categoria do conteúdo é texto.|  
|FontFamily (legível não modificável)|A propriedade da família de fonte do elemento TextBlock não pode ser alterada, mas é visível para o localizador.|  
  
|Comentários de forma livre de localização|Significado|  
|--------------------------------------|-------------|  
|$Content (Marca registrada)|O criador do aplicativo informa o localizador que o conteúdo no elemento TextBlock é uma marca registrada.|  
|FontSize (Tamanho da fonte da marca registrada)|O criador do aplicativo indica que a propriedade de tamanho da fonte deve seguir o tamanho padrão de marcas registradas.|  
  
### <a name="localizability-attributes"></a>Atributos de possibilidade de localização  
 As informações em Localization.Attributes contém uma lista de pares: o nome do valor de destino e os valores associados de possibilidade de localização. O nome do destino pode ser um nome de propriedade ou o nome especial de $Content. Se for um nome de propriedade, o valor de destino será o valor da propriedade. Se for $Content, o valor de destino será o conteúdo do elemento.  
  
 Há três tipos de atributos:  
  
- **Categoria**. Especifica se um valor deve ser modificável de uma ferramenta do localizador. Consulte <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Legibilidade**. Especifica se uma ferramenta do localizador deve ler (e exibir) um valor. Consulte <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Modificabilidade**. Especifica se uma ferramenta do localizador permite que um valor seja modificado. Consulte <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Esses atributos podem ser especificados em qualquer ordem delimitada por um espaço. No caso de atributos duplicados serem especificados, o último atributo substituirá os antigos. Por exemplo, Localization.Attributes = "Modificável não modificável" define Modificabilidade como Modificável porque é o último valor.  
  
 Modificabilidade e Legibilidade são autoexplicativos. O atributo Categoria fornece categorias predefinidas que ajudam o localizador durante a tradução do texto. As categorias, como Texto, Rótulo e Título, fornecem informações ao localizador sobre como traduzir o texto. Também há categorias especiais: Nenhum, herdar, ignorar e NeverLocalize.  
  
 A tabela a seguir mostra o significado das categorias especiais.  
  
|Categoria|Significado|  
|--------------|-------------|  
|Nenhum|O valor de destino não tem nenhuma categoria definida.|  
|Herdar|O valor de destino herda sua categoria de seu pai.|  
|Ignorar|O valor de destino é ignorado no processo de localização. Ignorar afeta somente o valor atual. Ela não afetará os nós filho.|  
|NeverLocalize|O valor atual não pode ser localizado. Esta categoria é herdada pelos filhos de um elemento.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Comentários de localização  
 Localization.Comments contém cadeias de caracteres de formato livre sobre o valor de destino. Os desenvolvedores de aplicativos podem adicionar informações para fornecer dicas aos localizadores sobre como o texto dos aplicativos deve ser traduzido. O formato dos comentários pode ser qualquer cadeia de caracteres cercada por "()". Use '\\' para os caracteres de escape.  
  
## <a name="see-also"></a>Consulte também

- [Globalização para WPF](globalization-for-wpf.md)
- [Usar layout automático para criar um botão](how-to-use-automatic-layout-to-create-a-button.md)
- [Usar uma grade para layout automático](how-to-use-a-grid-for-automatic-layout.md)
- [Localizar um aplicativo](how-to-localize-an-application.md)
