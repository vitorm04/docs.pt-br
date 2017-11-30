---
title: "Arquivo especificado no nome do arquivo não é um arquivo XML válido"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3275608a1871ac981eb5b3aa39f0be6ab4e758e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Arquivo especificado no nome do arquivo não é um arquivo XML válido
O nome do arquivo que você forneceu não é um arquivo XML válido. Para especificar a estrutura permitida e o conteúdo de um documento XML, você pode usar uma definição de tipo de documento (DTD), um esquema Microsoft XML-Data Reduced (XDR) ou um esquema de linguagem XSD de definição de esquema XML. Esquemas XSD são a melhor maneira de especificar gramáticas XML no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
>  Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets tipados e esquema XML. O **XML Designer** ainda pode ser usado para criar e editar arquivos de esquema XML. No entanto, em [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], o designer para criar e editar conjuntos de dados tipados é o **Dataset Designer**. Para obter mais informações, consulte [criando e editando conjuntos de dados digitados](/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se você está fornecendo o nome de arquivo correto.  
  
-   Verifique se o arquivo especificado contém XML válido ao carregar o arquivo XML que você deseja verificar para o **XML Designer**. Do **XML** menu, clique em **Validar XML**. Erros são exibidos no **lista de tarefas**.  
  
-   Se o arquivo XML tem um esquema XML associado, verifique se os elementos aparecem na estrutura definida e que o conteúdo dos elementos individuais está de acordo com os tipos de dados declarado especificados no esquema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml>  
 [Como analisar demarcadores de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
