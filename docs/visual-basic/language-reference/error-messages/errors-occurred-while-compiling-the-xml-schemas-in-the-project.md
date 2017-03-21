---
title: Ocorreram erros ao compilar os esquemas XML no projeto | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
dev_langs:
- VB
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cf04e85da98db53d1c78269169571936f708cd21
ms.lasthandoff: 03/13/2017

---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Ocorreram erros na compilação dos esquemas XML no projeto
Ocorreram erros ao compilar os esquemas XML no projeto. Por isso, o XML IntelliSense não está disponível.  
  
 Há um erro em um esquema de definição de esquema XML (XSD) incluído no projeto. Esse erro ocorre quando você adiciona um arquivo de esquema (. xsd) de XSD que está em conflito com o esquema XSD existente definido para o projeto.  
  
 **ID do erro:** BC36810  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Clique duas vezes no aviso no **lista de erros** janela. Visual Basic levará você para o local no arquivo XSD que é a origem do aviso. Corrija o erro no esquema XSD.  
  
-   Garantir que todos os arquivos de esquema (. xsd) de XSD são incluídos no projeto. Talvez você precise clicar em **Show All Files** no **projeto** arquivos para ver seu. xsd em **Solution Explorer**. Clique em um arquivo. xsd e, em seguida, clique em **incluir no projeto** para incluir o arquivo no seu projeto.  
  
-   Se você estiver usando o Assistente de XML para esquema, esse erro pode ocorrer se você inferir esquemas mais de uma vez da mesma fonte. Nesse caso, você pode remover os arquivos de esquema XSD existentes do projeto, adicione um novo XML ao modelo de item de esquema e forneça o XML para Assistente de esquema com todas as fontes XML aplicáveis para o seu projeto.  
  
-   Se nenhum erro for identificado no seu esquema XSD, o compilador XML pode não ter informações suficientes para fornecer uma mensagem de erro detalhada. Você poderá obter informações mais detalhadas de erro se você garantir que namespaces XML para os arquivos. xsd incluídos em seu projeto correspondam a namespaces XML identificados para o esquema XML definido no Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Janela lista de erros](https://docs.microsoft.com/visualstudio/ide/reference/error-list-window)   
 [XML IntelliSense no Visual Basic](../../../visual-basic/programming-guide/language-features/xml/xml-intellisense.md)   
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)
