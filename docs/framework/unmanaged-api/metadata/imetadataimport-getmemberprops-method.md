---
title: IMetaDataImport::GetMemberProps (Método)
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetmemberprops-method"></a>IMetaDataImport::GetMemberProps (Método)
Obtiene información de metadatos, incluidos el nombre, la firma binaria y la dirección virtual relativa, de la <xref:System.Type> miembro al que hace referencia el token de metadatos especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mb`  
 [in] El token que hace referencia al miembro para obtener los metadatos asociados.  
  
 `pClass`  
 [out] Un puntero al token de metadatos que representa la clase del miembro.  
  
 `szMember`  
 [out] El nombre del miembro.  
  
 `cchMember`  
 [in] El tamaño en caracteres anchos de la `szMember` búfer.  
  
 `pchMember`  
 [out] El tamaño en caracteres anchos del nombre devuelto.  
  
 `pdwAttr`  
 [out] Los valores de marca que se aplica al miembro.  
  
 `ppvSigBlob`  
 [out] Un puntero a la firma de metadatos binaria del miembro.  
  
 `pcbSigBlob`  
 [out] El tamaño en bytes de `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Un puntero a la dirección virtual relativa del miembro.  
  
 `pdwImplFlags`  
 [out] Los marcadores de implementación de método asociados al miembro.  
  
 `pdwCPlusTypeFlag`  
 [out] Un indicador que marca un <xref:System.ValueType>.  
  
 `ppValue`  
 [out] Un valor de cadena constante devuelto por este miembro.  
  
 `pcchValue`  
 [out] El tamaño en caracteres de `ppValue`, o cero si `ppValue` no contiene una cadena.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Encabezado:** Cor.h  
  
 **Biblioteca:** incluye como recurso en MsCorEE.dll  
  
 **Versiones de .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [IMetaDataImport (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
