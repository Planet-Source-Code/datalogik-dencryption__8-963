<div align="center">

## dEncryption


</div>

### Description

It will encrypt/decrypt a string with the given variables.
 
### More Info
 
$dString is the string you wish to encrypt

$dKey is your encryption key

$dType is to encrypt or decrypt the string ($dType values are 0 or 1,

0 is encrypt and 1 is decrypt)

$dIntense is how many times you wish to encrypt the

string (makes for a more secure and harder to break string)

Since the highest ascii value for a text character is 255, if

you set the $dIntense value to 255, it will just loop back to

where it was, and intern decrypt what you encrypted.

$dCalcNum is the number that will be added or subtracted with when

ever encryption begins. The math will take place and will affect

the first ascii number in the two statements.

Returns the crypted string.

If the user defines the $dIntense variable to 255, it will not work properly.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[datalogik](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/datalogik.md)
**Level**          |Intermediate
**User Rating**    |4.5 (45 globes from 10 users)
**Compatibility**  |PHP 3\.0, PHP 4\.0
**Category**       |[Algorithims](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/algorithims__8-29.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/datalogik-dencryption__8-963/archive/master.zip)

### API Declarations

Copyright 2003 Jonathan Anders


### Source Code

```
<?php
	/*
	Title:
	 dEncryption
	Version:
	 v3
	Description:
	 An encryption algorithm with a few twists that I have added.
	Author:
	 Jonathan Anders
	 datalogik@datalogik.org
	 http://www.datalogik.org
	Usage:
	 function CryptAlg($dString,$dKey,$dType,$dIntense,$dCalcNum)
	 * Where:
	  $dString is the string you wish to encrypt
	  $dKey is your encryption key
	  $dType is to encrypt or decrypt the string ($dType values are 0 or 1,
		0 is encrypt and 1 is decrypt)
	  $dIntense is how many times you wish to encrypt the
		string (makes for a more secure and harder to break string)
		Since the highest ascii value for a text character is 255, if
		you set the $dIntense value to 255, it will just loop back to
		where it was, and intern decrypt what you encrypted.
	  $dCalcNum is the number that will be added or subtracted with when
		ever encryption begins. The math will take place and will affect
		the first ascii number in the two statements.
	Notes:
	 When crypting a string, remember that you MUST have the exact
	 same $dKey, $dIntense, and $dCalcNum variables as the encrypted
	 or decrypted string for it to accurately do it's job.
	*/
	function CryptAlg($dString,$dKey,$dType,$dIntense,$dCalcNum)
	{
		if ($dIntense > 254)
			$dIntense = 254;
		$dNewString = $dString;
		for ($y = 0; $y <= $dIntense; $y++)
		{
			$strOutput = "";
			$x = 0;
			for ($i = 0; $i < strlen($dNewString); $i++)
			{
				if ($x >= strlen($dKey))
					$x = 0;
				if ($dType == 0)
					$strOutput .= Chr((Ord($dNewString[$i]) + $dCalcNum) - Ord($dKey[$x]));
				if ($dType == 1)
					$strOutput .= Chr((Ord($dNewString[$i]) - $dCalcNum) + Ord($dKey[$x]));
				$x++;
			}
			$dNewString = $strOutput;
		}
		return $dNewString;
	}
	$test = CryptAlg("Crypt Algorithm", "testkey1234567890", 0, 110, 1234567890);
	echo "Encrypted text: $test<br>";
	$test = CryptAlg($test, "testkey1234567890", 1, 110, 1234567890);
	echo "Decrypted text: $test<br>";
?>
```

