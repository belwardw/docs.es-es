---
title: "GetCORVersion (Función)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORVersion
helpviewer_keywords: GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6218714030892531f3b9ed4b4a79917347d250db
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2017
---
# <a name="getcorversion-function"></a><span data-ttu-id="ef42f-102">GetCORVersion (Función)</span><span class="sxs-lookup"><span data-stu-id="ef42f-102">GetCORVersion Function</span></span>
<span data-ttu-id="ef42f-103">Devuelve el número de versión de common language runtime (CLR) que se ejecuta en el proceso actual.</span><span class="sxs-lookup"><span data-stu-id="ef42f-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="ef42f-104">Esta función está desusada en [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ef42f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef42f-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ef42f-105">Syntax</span></span>  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="ef42f-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ef42f-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="ef42f-107">Un puntero a un búfer en el que CLR devuelve una cadena que especifica la versión del runtime que está cargada actualmente en el proceso.</span><span class="sxs-lookup"><span data-stu-id="ef42f-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="ef42f-108">La cadena devuelta adopta el mismo formato como cadenas que se pasan al [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), por ejemplo, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="ef42f-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="ef42f-109">Si el tiempo de ejecución aún no se han cargado en el proceso, la función devuelve la información de directorio adecuado para la versión más reciente del runtime instalada en el equipo.</span><span class="sxs-lookup"><span data-stu-id="ef42f-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ef42f-110">El número de caracteres (`WCHAR`s) que se pueden guardar en `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="ef42f-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ef42f-111">Un puntero al número de caracteres devueltos realmente en `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="ef42f-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="ef42f-112">Si `pbuffer` es un puntero nulo, el tiempo de ejecución devuelve E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="ef42f-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="ef42f-113">Si el número de caracteres es mayor, a continuación, la longitud de `pbuffer` , el tiempo de ejecución devuelve ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="ef42f-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef42f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef42f-114">Requirements</span></span>  
 <span data-ttu-id="ef42f-115">**Plataformas:** vea [requisitos del sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef42f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef42f-116">**Encabezado:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ef42f-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ef42f-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ef42f-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef42f-118">**Versiones de .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef42f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef42f-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="ef42f-119">See Also</span></span>  
 [<span data-ttu-id="ef42f-120">Funciones de hospedaje de CLR en desuso</span><span class="sxs-lookup"><span data-stu-id="ef42f-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)