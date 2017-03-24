---
title: "Arquivo especificado no nome do arquivo não é um arquivo XML válido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2fa595ab411fdd300327db9e1fcca1e3156c7eed
ms.lasthandoff: 03/13/2017

---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Arquivo especificado no nome do arquivo não é um arquivo XML válido
O nome do arquivo que você forneceu não é um arquivo XML válido. Para especificar a estrutura permitida e o conteúdo de um documento XML, você pode usar uma definição de tipo de documento (DTD), um esquema de Microsoft XML-Data Reduced (XDR) ou um esquema de linguagem XSD de definição de esquema XML. Esquemas XSD são a melhor maneira de especificar gramáticas XML no [!INCLUDE[dnprdnshort](../../csharp/getting-started/includes/dnprdnshort_md.md)].  
  
> [!NOTE]
>  Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets digitados e esquema XML. O **XML Designer** ainda pode ser usado para criar e editar arquivos de esquema XML. No entanto, em [!INCLUDE[vs_current_long](../../csharp/misc/includes/vs_current_long_md.md)], o designer para criar e editar conjuntos de dados tipados é o **Dataset Designer**. Para obter mais informações, consulte [criando e editando conjuntos de dados tipados](https://docs.microsoft.com/visualstudio/data-tools/creating-and-editing-typed-datasets).  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se você está fornecendo o nome de arquivo correto.  
  
-   Verifique se o arquivo especificado contém XML válido ao carregar o arquivo XML que você deseja verificar para o **XML Designer**. Do **XML** menu, clique em **Validar XML**. Erros são exibidos no **lista de tarefas**.  
  
-   Se o arquivo XML tem um esquema XML associado, verifique se os elementos aparecem na estrutura definida e que o conteúdo dos elementos individuais em conformidade com os tipos de dados declarados especificados no esquema.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Xml></xref:System.Xml>   
 [Como analisar demarcadores de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
