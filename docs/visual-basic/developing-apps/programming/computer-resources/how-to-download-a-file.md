---
title: "Como baixar um arquivo no Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "baixando arquivos"
  - "baixando recursos de Internet, Arquivos "
  - "Arquivos , baixando"
  - "Arquivos , transferindo"
  - "computadores remotos, baixando de"
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como baixar um arquivo no Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

O <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> método pode ser usado para baixar um arquivo remoto e armazená\-lo em um local específico.  Se o parâmetro `ShowUI` estiver definido como `True`, uma caixa de diálogo será exibida mostrando o andamento do download e permitindo que usuários cancelem a operação.  Por padrão, arquivos existentes com o mesmo nome não são sobrescritos; se você deseja sobrescrever arquivos existentes, defina o parâmetro `overwrite` como `True`.  
  
 As seguintes condições podem causar uma exceção:  
  
-   Nome da unidade é inválido \(<xref:System.ArgumentException>\).  
  
-   Autenticação necessária não foi fornecida \(<xref:System.UnauthorizedAccessException> ou <xref:System.Security.SecurityException>\).  
  
-   O servidor não responde dentro do `connectionTimeout` especificado \(<xref:System.TimeoutException>\).  
  
-   A solicitação foi negada pelo Web site \(<xref:System.Net.WebException>\).  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
> [!IMPORTANT]
>  Não faça decisões sobre o conteúdo do arquivo com base no nome do arquivo.  Por exemplo, o arquivo Form1.vb pode não ser um arquivo fonte do Visual Basic.  Verifique todas as entradas antes de usar os dados no seu aplicativo.  O conteúdo do arquivo pode não ser esperado e métodos para ler o arquivo podem falhar.  
  
### Para baixar um arquivo  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando a localidade do arquivo de destino como uma sequência de caracteres ou URI e especificando a localidade na qual se deseja armazenar o arquivo.  Este exemplo faz o download do arquivo `WineList.txt` a partir de `http://www.cohowinery.com/downloads` e o salva em `C:\Documents and Settings\All Users\Documents`:  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### Para baixar um arquivo, especificando um intervalo de tempo limite  
  
-   Use o método `DownloadFile` para baixar o arquivo, especificando a localidade do arquivo de destino como uma sequência de caracteres ou URI, especificando a localidade na qual se deseja armazenar o arquivo, e especificando o intervalo de tempo limite em milissegundos \(o padrão é 1000\).  Este exemplo faz o download do arquivo `WineList.txt` a partir de `http://www.cohowinery.com/downloads` e o salva em `C:\Documents and Settings\All Users\Documents`, especificando um intervalo de tempo limite de 500 milissegundos:  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### Para baixar um arquivo, fornecendo um nome de usuário e senha  
  
-   Use o método `DownLoadFile` para baixar o arquivo, especificando a localidade do arquivo de destino como uma sequência de caracteres ou URI e especificando a localidade na qual se deseja armazenar o arquivo.  Este exemplo faz o download do arquivo `WineList.txt` a partir de `http://www.cohowinery.com/downloads` e o salva em `C:\Documents and Settings\All Users\Documents`, com o nome de usuário `anonymous` e uma senha em branco.  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  O protocolo FTP usado pelo método `DownLoadFile` envia informações, incluindo senhas, em texto sem\-formatação e não deve ser usado para transmitir informações confidenciais.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [Como carregar um arquivo](../Topic/How%20to:%20Upload%20a%20File%20in%20Visual%20Basic.md)   
 [Como analisar caminhos de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)