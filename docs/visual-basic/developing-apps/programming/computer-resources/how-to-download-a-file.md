---
title: Como baixar um arquivo no Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- downloading Internet resources, files
- downloading files
- remote computers, downloading from
- files, downloading
- files, transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bd37b52d12876dad6ec4b2a1bb34f4987f933c08
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-download-a-file-in-visual-basic"></a>Como baixar um arquivo no Visual Basic
O método <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> pode ser usado para baixar um arquivo remoto e armazená-lo em um local específico. Se o parâmetro `ShowUI` for definido como `True`, uma caixa de diálogo será exibida mostrando o andamento do download e permitindo que os usuários cancelem a operação. Por padrão, os arquivos existentes com o mesmo nome não são sobrescritos. Se você deseja sobrescrever os arquivos existentes, defina o parâmetro `overwrite` como `True`.  
  
 As seguintes condições podem causar uma exceção:  
  
-   O nome da unidade não é válido (<xref:System.ArgumentException>).  
  
-   A autenticação necessária não foi fornecida (<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>).  
  
-   O servidor não responde dentro do `connectionTimeout` especificado (<xref:System.TimeoutException>).  
  
-   A solicitação é negada pelo site (<xref:System.Net.WebException>).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo Form1.vb pode não ser um arquivo de código-fonte do Visual Basic. Verifique todas as entradas antes de usar os dados no seu aplicativo. O conteúdo do arquivo pode não ser esperado, e os métodos para ler o arquivo podem falhar.  
  
### <a name="to-download-a-file"></a>Para baixar um arquivo  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI e especificando o local no qual armazenar o arquivo. Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>Para baixar um arquivo, especificando um intervalo de tempo limite  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o intervalo de tempo limite, em milissegundos (o padrão é 1000). Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva-o em `C:\Documents and Settings\All Users\Documents`, especificando um intervalo de tempo limite de 500 milissegundos:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>Para baixar um arquivo, fornecendo um nome de usuário e senha  
  
-   Use o método `DownLoadFile` para baixar o arquivo, especificando o local do arquivo de destino como uma cadeia de caracteres ou URI, especificando o local no qual armazenar o arquivo e especificando o nome de usuário e a senha. Este exemplo baixa o arquivo `WineList.txt` de `http://www.cohowinery.com/downloads` e salva em `C:\Documents and Settings\All Users\Documents`, com o nome de usuário `anonymous` e uma senha em branco.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  O protocolo FTP usado pelo método `DownLoadFile` envia informações, incluindo senhas, em texto sem formatação e não deve ser usado para transmitir informações confidenciais.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [Como carregar um arquivo](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

