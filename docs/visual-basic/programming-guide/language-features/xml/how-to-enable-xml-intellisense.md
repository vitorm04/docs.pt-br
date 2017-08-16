---
title: 'Como: habilitar o XML IntelliSense no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- XML IntelliSense [Visual Basic]
- XML [Visual Basic], IntelliSense
- IntelliSense [Visual Basic], XML
ms.assetid: af67d0ee-a4a6-4abf-9c07-5a8cfe80d111
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 84af19189fa3fc510c8d4f8e408cbb2a393d8b8f
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-enable-xml-intellisense-in-visual-basic"></a>Como habilitar o IntelliSense XML no Visual Basic
XML IntelliSense no Visual Basic fornece preenchimento automático de palavras para os elementos que são definidos em um esquema XML. Para habilitar o XML IntelliSense no Visual Basic, você deve fazer o seguinte:  
  
1.  Obter o arquivo de esquema (XSD) XML ou arquivos para os arquivos XML que seu aplicativo irá ler ou gravar.  
  
2.  Inclua os arquivos de esquema XML em seu projeto.  
  
3.  Importe o namespace de destino ou espaços para nome para seu arquivo de código ou projeto. Um namespace de destino é identificado pelo `targetNamespace` ou `tns` atributo do esquema XSD.  
  
     Para importar um namespace de destino, use o `Imports` instrução, ou adicionar um namespace para todos os arquivos de código em um projeto usando o **referências** página do Project Designer.  
  
 Para obter mais informações sobre os recursos do IntelliSense XML no Visual Basic, consulte [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md). Para obter mais informações sobre como importar namespaces XML, consulte [instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) ou [referências de página, Designer de projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
 ![link para vídeo](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") para uma versão em vídeo deste tópico, consulte [vídeo como: habilitar o XML IntelliSense no Visual Basic](http://go.microsoft.com/fwlink/?LinkId=102466). Para uma demonstração em vídeo relacionada, consulte [como faço para habilitar XML IntelliSense e Namespaces de XML de uso?](http://go.microsoft.com/fwlink/?LinkId=143035).  
  
## <a name="enable-xml-intellisense-in-visual-basic"></a>Habilitar o IntelliSense XML no Visual Basic  
 Se você tiver um arquivo XML, mas você não tem um arquivo de esquema XSD para ele, no SP1 você pode criar um arquivo de esquema XSD usando o Assistente de XML para esquema. Você também pode usar inferência de esquema no Editor de XML do Visual Studio.  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-the-xml-to-schema-wizard-requires-sp1"></a>Para criar um arquivo de esquema XSD para um arquivo XML usando o Assistente de XML para esquema (requer SP1)  
  
1.  Em seu projeto, clique em **Adicionar Novo Item** sobre o **projeto** menu.  
  
2.  Selecione o **Xml para esquema** modelo de item do **dados** ou **itens comuns** categorias de modelo.  
  
3.  Forneça um nome de arquivo para o arquivo XSD ou arquivos que o conjunto de esquema inferido serão armazenados em e, em seguida, clique em **adicionar**.  
  
4.  No **inferir esquema XML definido de documentos XML** janela, adicione um ou mais documentos XML para inferir o esquema XML definido de.  
  
    -   Para adicionar arquivos de texto que contêm documentos XML usando o Explorador de arquivos, clique em **adicionar de arquivo**.  
  
    -   Para adicionar um documento XML de um endereço HTTP, clique em **adicionar da Web**.  
  
    -   Para copiar ou digitar o conteúdo de um documento XML no assistente, clique em **digitar ou colar XML**.  
  
5.  Quando você tiver especificado todas as fontes de documento XML do qual você deseja inferir o conjunto de esquema XML, clique em **Okey** inferir o esquema XML definido. O conjunto de esquema é salvo na pasta do projeto em um ou mais arquivos XSD. (Para cada namespace XML no esquema, um arquivo é criado.)  
  
#### <a name="to-create-an-xsd-schema-file-for-an-xml-file-by-using-schema-inference-in-the-visual-studio-xml-editor"></a>Para criar um arquivo de esquema XSD para um arquivo XML usando inferência de esquema no Editor de XML do Visual Studio  
  
1.  Edite o arquivo XML Designer XML do Visual Studio.  
  
2.  Quando o cursor estiver em algum lugar no arquivo XML, o **XML** menu é exibido. Clique em **Create Schema** sobre o **XML** menu. É criado um arquivo XSD do esquema XSD inferida do arquivo XML.  
  
3.  Salve o arquivo de esquema XSD.  
  
    > [!NOTE]
    >  Diferentes esquemas XSD podem ser inferidas de vários documentos XML que devem ter o mesmo esquema. Isso pode ocorrer quando determinados elementos e atributos são encontrados em um arquivo XML e não no outro, ou quando estiver incluído em uma ordem diferente, por exemplo. Você deve revisar esquemas XSD inferidos para a integridade e a precisão quando você usa a inferência de esquema XSD.  
  
#### <a name="to-include-an-xsd-schema-file"></a>Para incluir um arquivo de esquema XSD  
  
-   Por padrão, é possível ver os arquivos XSD em projetos do Visual Basic. Se o arquivo XSD já está incluído nas pastas de seu projeto, clique o **Show All Files** no botão **Solution Explorer**. Localize o arquivo XSD em **Solution Explorer**, clique no arquivo e clique em **incluir o arquivo no projeto**.  
  
-   Se o arquivo XSD já não é parte do seu projeto, em **Solution Explorer**, clique na pasta na qual você deseja armazenar o arquivo XSD, aponte para **adicionar**e, em seguida, clique em **Item existente**. Localize o arquivo XSD e, em seguida, clique em **adicionar**.  
  
#### <a name="to-import-an-xml-namespace-in-a-code-file"></a>Para importar um namespace XML em um arquivo de código  
  
1.  Identifique o namespace de destino do esquema XSD.  
  
2.  No início do arquivo de código, adicione um `Imports` declaração para o namespace XML de destino, conforme mostrado no exemplo a seguir.  
  
     [!code-vb[VbXMLSamples n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_1.vb)]  
  
     Para importar um namespace XML como o namespace padrão, ou seja, o namespace que é aplicado a elementos XML e atributos que não têm um prefixo de namespace, adicione um `Imports` declaração do namespace de destino padrão XML. Não especifique um prefixo de namespace. A seguir está um exemplo de uma `Imports` instrução.  
  
     [!code-vb[VbXmlSamples&#50;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-enable-xml-intellisense_2.vb)]  
  
#### <a name="to-import-an-xml-namespace-for-all-files-in-a-project"></a>Para importar um namespace XML para todos os arquivos em um projeto  
  
1.  Um namespace XML importado em um arquivo de código aplica-se somente nesse arquivo de código. Para importar um namespace XML que se aplica a todos os arquivos de código em um projeto, abra o Project Designer clicando duas vezes em **meu projeto** na **Solution Explorer**.  
  
2.  Sobre o **referências** guia o **importado namespaces** , digite o namespace de XML de destino na forma de uma declaração de namespace XML completa (por exemplo, `<xmlns: ns="http://sampleNamespace">`). Se o namespace de XML de destino não especificar um prefixo de namespace, o namespace será o namespace XML padrão para o projeto.  
  
3.  Clique em **Adicionar importação de usuário**.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Imports (Namespace XML)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [Página Referências, Designer de Projeto (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)   
 [XML IntelliSense no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)

