---
title: Arquivo especificado no nome de arquivo não é um arquivo XML válido
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: 89499b07e767bd0b3a777db4e5155f64a4357f0c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052307"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a>Arquivo especificado no nome de arquivo não é um arquivo XML válido

O nome do arquivo que você forneceu não é um arquivo XML válido. Para especificar a estrutura permitida e conteúdo de um documento XML, você pode usar uma definição de tipo de documento (DTD), um esquema do Microsoft XML-Data Reduced (XDR) ou um esquema XSD (linguagem) de definição de esquema XML. Esquemas XSD são a maneira preferencial para especificar as gramáticas XML no [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].

> [!NOTE]
> Em algumas versões anteriores do Visual Studio, o **XML Designer** é o designer para datasets tipados e esquema XML. O **XML Designer** ainda pode ser usado para criar e editar arquivos de esquema XML. No entanto, no Visual Studio 2012, o designer para criar e editar datasets tipados é o **Dataset Designer**. Para obter mais informações, consulte [criando e editando conjuntos de dados tipados](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Verifique se você está fornecendo o nome de arquivo correto.

- Verifique se o arquivo especificado contém um XML válido ao carregar o arquivo XML que você deseja verificar para o **XML Designer**. Dos **XML** menu, clique em **Validar XML**. Erros são exibidos na **lista de tarefas**.

- Se o arquivo XML tem um esquema XML associado, verifique que os elementos são exibidos na estrutura definida e que o conteúdo dos elementos individuais está de acordo com os tipos de dados declarado especificados no esquema.

## <a name="see-also"></a>Consulte também

- <xref:System.Xml>
- [Como: Analisar caminhos de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)