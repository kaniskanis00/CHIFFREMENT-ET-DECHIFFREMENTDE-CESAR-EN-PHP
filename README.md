# CHIFFREMENT-CESAR-EN-PHP
<?php
function chiffrementCesar($texte, $decalage) {
    $chiffre = '';

    for ($i = 0; $i < strlen($texte); $i++) {
        $caractere = $texte[$i];

        if (ctype_alpha($caractere)) {
            $majuscule = ctype_upper($caractere);
            $caractere = strtoupper($caractere);

            $caractereDechiffre = ord($caractere) - ord('A');
            $caractereChiffre = ($caractereDechiffre + $decalage) % 26;

            $caractereChiffre = ($caractereChiffre < 0) ? $caractereChiffre + 26 : $caractereChiffre;

            $caractereChiffre += ord('A');

            $caractere = chr($caractereChiffre);

            if (!$majuscule) {
                $caractere = strtolower($caractere);
            }
        }

        $chiffre .= $caractere;
    }

    return $chiffre;
}

$texte = "Bonjour le monde";
$decalage = 3;

$texteChiffre = chiffrementCesar($texte, $decalage);

echo "Texte initial : $texte\n";
echo "Texte chiffré : $texteChiffre\n";
?>

# ET-DECHIFFREMENTDE-CESAR-EN-PHP

<?php
function dechiffrementCesar($texteChiffre, $decalage) {
    return chiffrementCesar($texteChiffre, -$decalage);
}

$texteDechiffre = dechiffrementCesar($texteChiffre, $decalage);

echo "Texte déchiffré : $texteDechiffre\n";
?>
