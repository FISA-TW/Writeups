# 2016 AIS3 pre-exam : Crypto2
Category: Crypto, Points: 2  

## Description
Give you a url, please find the code.

## Write-up
�u�CWeb4�A�h���D�ئ��|�}...(ry  
�i������A�|�o�{���}�h�Fexpire��auth�A�e�̬O�ھڲ{�b��unix timestamp�ͦ��A�᭱�h�O��flag+expire=`$expire`�h��sha1 hash�ͦ����A�����W�|��ܳo�@����l�X�]�����^�A�J�Ӭݷ|�o�{�Ĥ@��if�������P�_��``if(sha1($secret . "$qstr") === $auth)``�M�̤U����else�ͦ���expire��auth�O�@�˪��A�]���A���󦡬O���ߪ��C�ߤ@�S�����ߪ��O�̸̭���``if($expire < time(0))``�A���ɷ|�o�{$expire�M$qstr���M���O��expire=xxx�A���O������k���@�ˡA$expire�O�z�L$_GET�ӥh������}���̫�@��expire�ܼơA��$qstr�h�O���"?"�᭱�Ĥ@��expire=xxx�A�]���b���}�̫᭱�[�W``&expire=9999999999999999``�N�i�H���Q�Ѷ}����flag�I  

## Keypoint
- �F��PHP��z