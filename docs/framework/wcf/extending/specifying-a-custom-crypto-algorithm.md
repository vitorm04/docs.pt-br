---
title: Especificando um algoritmo de criptografia personalizada
ms.date: 03/30/2017
ms.assetid: d662a305-8e09-451d-9a59-b0f12b012f1d
ms.openlocfilehash: 673d177a665e265d77f0221e0a00f4b814c8795c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186484"
---
# <a name="specifying-a-custom-crypto-algorithm"></a>Especificando um algoritmo de criptografia personalizada
O WCF permite que você especifique um algoritmo cripto personalizado para usar ao criptografar dados ou computar assinaturas digitais. Isso é feito pelas seguintes etapas:  
  
1. Derivar uma classe de<xref:System.ServiceModel.Security.SecurityAlgorithmSuite>  
  
2. Registre o algoritmo  
  
3. Configure a vinculação com a <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>classe derivada.  
  
## <a name="derive-a-class-from-securityalgorithmsuite"></a>Obtenha uma classe de SecurityAlgorithmSuite  
 A <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> é uma classe base abstrata que permite especificar o algoritmo para usar ao executar várias operações relacionadas à segurança. Por exemplo, calcular um hash para uma assinatura digital ou criptografar uma mensagem. O código a seguir mostra <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>como derivar uma classe de :  
  
```csharp  
public class MyCustomAlgorithmSuite : SecurityAlgorithmSuite  
    {  
        public override string DefaultAsymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaOaepKeyWrap; }  
        }  
  
        public override string DefaultAsymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.RsaSha1Signature; }  
        }  
  
        public override string DefaultCanonicalizationAlgorithm  
        {  
            get { return SecurityAlgorithms.ExclusiveC14n; ; }  
        }  
  
        public override string DefaultDigestAlgorithm  
        {  
            get { return SecurityAlgorithms.MyCustomHashAlgorithm; }  
        }  
  
        public override string DefaultEncryptionAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override int DefaultEncryptionKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSignatureKeyDerivationLength  
        {  
            get { return 128; }  
        }  
  
        public override int DefaultSymmetricKeyLength  
        {  
            get { return 128; }  
        }  
  
        public override string DefaultSymmetricKeyWrapAlgorithm  
        {  
            get { return SecurityAlgorithms.Aes128Encryption; }  
        }  
  
        public override string DefaultSymmetricSignatureAlgorithm  
        {  
            get { return SecurityAlgorithms.HmacSha1Signature; }  
        }  
  
        public override bool IsAsymmetricKeyLengthSupported(int length)  
        {  
            return length >= 1024 && length <= 4096;  
        }  
  
        public override bool IsSymmetricKeyLengthSupported(int length)  
        {  
            return length >= 128 && length <= 256;  
        }  
    }  
```  
  
## <a name="register-the-custom-algorithm"></a>Registre o Algoritmo Personalizado  
 O registro pode ser feito em um arquivo de configuração ou em código imperativo. O registro de um algoritmo personalizado é feito criando um mapeamento entre uma classe que implementa um provedor de serviços cripto e um alias. O alias é então mapeado para um URI que é usado ao especificar o algoritmo na vinculação do serviço WCF. O seguinte trecho de configuração ilustra como registrar um algoritmo personalizado na configuração:  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
           <cryptoClasses>  
              <cryptoClass SHA256CSP="System.Security.Cryptography.SHA256CryptoServiceProvider, System.Core, Version=3.5.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
           </cryptoClasses>  
           <nameEntry name="http://constoso.com/CustomAlgorithms/CustomHashAlgorithm"  
              class="SHA256CSP" />  
           </cryptoNameMapping>  
        </cryptographySettings>  
    </mscorlib>  
</configuration>  
```  
  
 A seção `cryptoClasses` sob o elemento <> cria o mapeamento entre o SHA256CryptoServiceProvider e o alias "SHA256CSP". O `nameEntry` elemento <> cria o mapeamento entre o alias "SHA256CSP" e a URL `http://constoso.com/CustomAlgorithms/CustomHashAlgorithm`especificada .  
  
 Para registrar o algoritmo personalizado <xref:System.Security.Cryptography.CryptoConfig.AddAlgorithm(System.Type,System.String[])> em código use o método. Este método cria ambos os mapeamentos. O exemplo a seguir mostra como chamar este método:  
  
```csharp
// Register the custom URI string defined for the hashAlgorithm in MyCustomAlgorithmSuite class to create the
// SHA256CryptoServiceProvider hash algorithm object.  
CryptoConfig.AddAlgorithm(typeof(SHA256CryptoServiceProvider), "http://constoso.com/CustomAlgorithms/CustomHashAlgorithm");  
```  
  
## <a name="configure-the-binding"></a>Configure a Vinculação  
 Você configura a vinculação especificando a classe derivada personalizada <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>nas configurações de vinculação, conforme mostrado no seguinte trecho de código:  
  
```csharp  
WSHttpBinding binding = new WSHttpBinding();  
            binding.Security.Message.AlgorithmSuite = new MyCustomAlgorithmSuite();  
```  
  
 Para obter um exemplo de código completo, consulte a amostra de Agilidade Criptográfica na amostra [WCF Security.](../samples/cryptographic-agility-in-wcf-security.md)  
  
## <a name="see-also"></a>Confira também

- [Protegendo serviços e clientes](../feature-details/securing-services-and-clients.md)
- [Protegendo serviços](../securing-services.md)
- [Visão geral da segurança](../feature-details/security-overview.md)
- [Conceitos de Segurança](../feature-details/security-concepts.md)
