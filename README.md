# dependent-dropdown-onchange.-where-second-dropdown-is-multiselect.

  $('#unit').change(function(){ 
                var unit=$(this).val();
               $.ajax({
                    url : "<?php echo base_url();?>index.php/CFController/getdistricts",
                    method : "POST",
                    data : {id: unit},
                    async : true,
                    dataType : 'json',
                    success: function(dsts){
//                        console.log(dsts);
                      $("#district").empty();
                       $.each(dsts, function(index, dst) {
                           console.log(dst);
                         $('#district ').append('<option value="'+ dst['cf002_distcode'] +'">'+ dst['cf002_distname'] +'</option>');
                        });
                         $('#district ').multiselect('rebuild');
                      }
                 }); 
                return false;
             
            }); 
