# nkf���C�u����
## �T�v
�t�@�C���Ȃǂ̕����R�[�h����肵����A�w��̕����R�[�h�ɕϊ�����Ƃ��������Ƃ��ł���B  

## �g�p��
### �����R�[�h����
�����R�[�h�𔻒肵�ďo�͂���ꍇ

    $ find -name 'JavaKadai031.java' | xargs nkf --guess

`find`�R�}���h�ŃJ�����g�f�B���N�g���ȉ���txt�t�@�C�������o�B  
���o���ʂ��p�C�v���C���Ŏ󂯓n���B  
`nkf`�̃I�v�V������`--guess`�Ńt�@�C���̏��o�́B  


### �����R�[�h�ϊ�
�����R�[�h��Shift-JIS�ɕϊ�����ꍇ  

    $ find -name '*.txt' | xargs nkf --overwrite -s

`find`�R�}���h�ŃJ�����g�f�B���N�g���ȉ���txt�t�@�C�������o�B  
���o���ʂ��p�C�v���C���Ŏ󂯓n���B  
`nkf`�̃I�v�V������`--overwrite`�Ńt�@�C���̏㏑���B  
`nkf`�̃I�v�V������`-s`��Shift-JIS���w�肵�ĕϊ��B  

