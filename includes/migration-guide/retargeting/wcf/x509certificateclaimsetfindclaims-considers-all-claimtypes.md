---
ms.openlocfilehash: 1ece2bb2d5e4ce93f201536d03aabeff5eb0012e
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804362"
---
### <a name="x509certificateclaimsetfindclaims-considers-all-claimtypes"></a>X509CertificateClaimSet.FindClaims considera todos os claimTypes

|   |   |
|---|---|
|Detalhes|Em aplicativos destinados ao .NET Framework 4.6.1, se um conjunto de declarações X509 for inicializado de um certificado que tenha várias entradas DNS em seu campo SAN, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> tentará corresponder o argumento claimType a todas as entradas DNS. Em aplicativos destinados a versões anteriores do .NET Framework, o método <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=name> tenta corresponder o argumento claimType somente com a última entrada DNS.|
|Sugestão|Essa alteração afeta apenas aplicativos destinados ao .NET Framework 4.6.1. Essa alteração pode ser desabilitada (ou habilitada se destinados a versões anteriores a 4.6.1) com a opção de compatibilidade [DisableMultipleDNSEntries](~/docs/framework/migration-guide/mitigation-x509certificateclaimset-findclaims-method.md#mitigation).|
|Escopo|Secundário|
|Versão|4.6.1|
|Tipo|Redirecionando|
|APIs afetadas|<ul><li><xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims(System.String,System.String)?displayProperty=nameWithType></li></ul>|

