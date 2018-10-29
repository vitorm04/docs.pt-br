---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: 0f35cb5c106d041a771d17a6e528cbbc1d38042b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187667"
---
# <a name="ftp"></a>FTP
O .NET Framework fornece suporte abrangente para o protocolo FTP com as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse>. Essas classes são derivadas de <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse>. Na maioria dos casos, as classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> fornecem tudo o que é necessário para fazer a solicitação, mas se você precisar acessar os recursos específicos ao FTP expostos como propriedades, poderá fazer a conversão de tipo dessas classes em <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.  
  
## <a name="examples"></a>Exemplos  
 Para obter mais informações, consulte os seguintes tópicos: [Como baixar arquivos com FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [Como carregar arquivos com FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md) e [Como listar o conteúdo do diretório com FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).  
  
## <a name="ftp-and-proxies"></a>FTP e proxies  
 Se um proxy (especificado pela propriedade <xref:System.Net.FtpWebRequest.Proxy%2A>) for um proxy HTTP, haverá suporte apenas para os comandos <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> e <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails>.  
  
## <a name="see-also"></a>Consulte também  
 [Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Amostra de tecnologia de cliente FTP](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [Amostra de tecnologia do Gerenciador de FTP](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [Usando protocolos de aplicativo](../../../docs/framework/network-programming/using-application-protocols.md)
