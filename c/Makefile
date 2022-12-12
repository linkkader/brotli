
NAME = brotli

OBJECTS_DIRECTORY = obj/

COMMON_DIRECTORY = common/

DEC_DIRECTORY = dec/

ENC_DIRECTORY = enc/

FUZZ_DIRECTORY = fuzz/

DEC_FILE = bit_reader.c decode.c     huffman.c    state.c

COMMON_FILE = constants.c                  context.c                                dictionary.c                 platform.c                   shared_dictionary.c          transform.c

ENC_FILE = backward_references.c        block_splitter.c             command.c                    compress_fragment_two_pass.c encoder_dict.c               histogram.c                  metablock.c\
           backward_references_hq.c     brotli_bit_stream.c          compound_dictionary.c        dictionary_hash.c            entropy_encode.c             literal_cost.c               static_dict.c\
           bit_cost.c                   cluster.c                    compress_fragment.c          encode.c                     fast_log.c                   memory.c                     utf8_util.c

FUZZ_FILE = decode_fuzzer.c     run_decode_fuzzer.c

HEADERS = include

FLAGS =  -Wall -Wextra -Werror

OBJS = $(addprefix $(OBJECTS_DIRECTORY)$(COMMON_DIRECTORY), $(COMMON_FILE:.c=.o)) $(addprefix $(OBJECTS_DIRECTORY)$(DEC_DIRECTORY), $(DEC_FILE:.c=.o)) $(addprefix $(OBJECTS_DIRECTORY)$(ENC_DIRECTORY), $(ENC_FILE:.c=.o)) $(addprefix $(OBJECTS_DIRECTORY)$(FUZZ_DIRECTORY), $(FUZZ_FILE:.c=.o))


$(OBJECTS_DIRECTORY)%.o : %.c
	gcc  $(FLAGS) -I $(HEADERS) -c $< -o $@

all:$(NAME)

$(OBJECTS_DIRECTORY):
	mkdir -p $@
	mkdir -p $(OBJECTS_DIRECTORY)$(OBJECTS_DIRECTORY)
	mkdir -p $(OBJECTS_DIRECTORY)$(COMMON_DIRECTORY)
	mkdir -p $(OBJECTS_DIRECTORY)$(DEC_DIRECTORY)
	mkdir -p $(OBJECTS_DIRECTORY)$(ENC_DIRECTORY)
	mkdir -p $(OBJECTS_DIRECTORY)$(FUZZ_DIRECTORY)

$(NAME): $(OBJECTS_DIRECTORY) $(OBJS)
	gcc $(FLAGS) -I $(HEADERS) $(OBJS)  -o  $(NAME)


clean:
	rm -Rf $(OBJECTS_DIRECTORY)


fclean: clean
	rm -f $(NAME)

re: fclean all

.PHONY: all clean fclean re
