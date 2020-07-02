---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614287"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="726e1-101">Segurança de transporte do WCF é compatível com certificados armazenados usando CNG</span><span class="sxs-lookup"><span data-stu-id="726e1-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="726e1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="726e1-102">Details</span></span>

<span data-ttu-id="726e1-103">Começando com os aplicativos destinados ao .NET Framework 4.6.2, a segurança de transporte do WCF é compatível com certificados armazenados usando a CNG (Biblioteca de Criptografia do Windows).</span><span class="sxs-lookup"><span data-stu-id="726e1-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="726e1-104">Esse suporte é limitado a certificados com uma chave pública que tenha um expoente não superior a 32 bits de comprimento.</span><span class="sxs-lookup"><span data-stu-id="726e1-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="726e1-105">Quando o aplicativo é destinado ao .NET Framework 4.6.2, esse recurso é ativado por padrão. Em versões anteriores do .NET Framework, a tentativa de usar os certificados X509 com um provedor de armazenamento de chaves CSG gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="726e1-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="726e1-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="726e1-106">Suggestion</span></span>

<span data-ttu-id="726e1-107">Os aplicativos destinados ao .NET Framework 4.6.1 e versões anteriores, mas que são executados no .NET Framework 4.6.2, podem habilitar a compatibilidade com os certificados CNG adicionando a seguinte linha à seção `<runtime>` do arquivo app.config ou web.config:</span><span class="sxs-lookup"><span data-stu-id="726e1-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="726e1-108">Isso também pode ser feito de modo programático com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="726e1-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="726e1-109">Observe que, por causa dessa alteração, qualquer código de tratamento de exceção que dependa da tentativa de iniciar a comunicação segura com um certificado CNG para falhar não será mais executado.</span><span class="sxs-lookup"><span data-stu-id="726e1-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="726e1-110">Name</span><span class="sxs-lookup"><span data-stu-id="726e1-110">Name</span></span>    | <span data-ttu-id="726e1-111">Valor</span><span class="sxs-lookup"><span data-stu-id="726e1-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="726e1-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="726e1-112">Scope</span></span>   | <span data-ttu-id="726e1-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="726e1-113">Minor</span></span>       |
| <span data-ttu-id="726e1-114">Versão</span><span class="sxs-lookup"><span data-stu-id="726e1-114">Version</span></span> | <span data-ttu-id="726e1-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="726e1-115">4.6.2</span></span>       |
| <span data-ttu-id="726e1-116">Type</span><span class="sxs-lookup"><span data-stu-id="726e1-116">Type</span></span>    | <span data-ttu-id="726e1-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="726e1-117">Retargeting</span></span> |
