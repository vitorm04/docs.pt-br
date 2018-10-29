---
title: Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
ms.date: 03/30/2017
helpviewer_keywords:
- SPC
- Software Publisher Certificate Test tool
- Software Publisher Certificate
- Cert2spc.exe
- certificates, Software Publisher's Certificate
ms.assetid: be434d7d-9c0d-46e7-8392-58a9b542d11d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75c782cbe7a45c05212c99448df6e8536a17f38d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202729"
---
# <a name="cert2spcexe-software-publisher-certificate-test-tool"></a>Cert2spc.exe (Ferramenta de Teste de Certificado do Fornecedor do Software)
A ferramenta Teste de Certificado do Editor de Software cria um SPC (Software Publisher's Certificate) com base em um ou vários certificados X.509. Cert2spc.exe é apenas para fins de teste. É possível obter um SPC válido de uma Autoridade de Certificação como, por exemplo, Verisign ou Thawte. Para obter mais informações sobre a criação de certificados X.509, consulte [Makecert.exe (Ferramenta de Criação de Certificado)](/windows/desktop/SecCrypto/makecert).  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7). Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 No prompt de comando, digite o seguinte:  
  
## <a name="syntax"></a>Sintaxe  
  
```  
cert2spc cert1.cer | crl1.crl [... certN.cer | crlN.crl] outputSPCfile.spc  
```  
  
#### <a name="parameters"></a>Parâmetros  
  
|Argumento|Descrição|  
|--------------|-----------------|  
|`certN.cer`|O nome de um certificado X.509 a ser incluído no arquivo SPC. É possível especificar vários nomes separados por espaços.|  
|`crlN.crl`|O nome de uma lista de revogações do certificado a ser incluída no arquivo SPC. É possível especificar vários nomes separados por espaços.|  
|`outputSPCfile.spc`|O nome do objeto PKCS #7 que conterá os certificados X.509.|  
  
|Opção|Descrição|  
|------------|-----------------|  
|**/?**|Exibe sintaxe de comando e opções para a ferramenta.|  
  
## <a name="examples"></a>Exemplos  
 O comando a seguir cria um SPC com base em `myCertificate.cer` e o coloca em `mySPCFile.spc`.  
  
```  
cert2spc myCertificate.cer mySPCFile.spc  
```  
  
 O comando a seguir cria um SPC com base em `oneCertificate.cer` e `twoCertificate.cer` e o coloca em `mySPCFile.spc`.  
  
```  
cert2spc oneCertificate.cer twoCertificate.cer mySPCFile.spc  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ferramentas](../../../docs/framework/tools/index.md)  
 [Makecert.exe (Ferramenta de Criação de Certificado)](/windows/desktop/SecCrypto/makecert)  
 [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
